---
name: watermarks-remover
description: >
  Remove multi-vendor AI provenance marks: invisible Unicode (Layer A), statistical
  text watermarks via rewrite (Layer B, always offer), and C2PA/EXIF/XMP/container
  metadata on PNG/JPEG/WebP/SVG/PDF/DOCX/ODT/HTML/MD. Covers Claude, Gemini/SynthID-class,
  OpenAI provenance, and open-LLM sampling marks. Use when the user asks to strip
  watermarks, remove C2PA/Content Credentials, clean AI metadata, remove invisible
  Unicode, anti-detect clean AI output, or runs /remove-ai-marks (aliases:
  /remove-claude-marks).
---

# Remove AI marks

Source: [guillaumemeyer/watermarks-remover](https://github.com/guillaumemeyer/watermarks-remover)

Multi-vendor anti-detection hygiene for **text** (Unicode + statistical rewrite) and **files** (C2PA / AI metadata across common containers).

Read if needed:

- `references/mark-classes.md` — Unicode / sampling / C2PA / containers
- `references/vendor-notes.md` — Claude, Gemini/SynthID, OpenAI, open-LLM
- `references/removal-matrix.md` — which layer when
- `references/ethics.md` — intended use
- `references/how-claude-marks.md` — Anthropic-specific detail
- `references/markdiffusion.md` — optional MarkDiffusion image harness (schemes, honesty caveats)

| Layer | Target | How |
| --- | --- | --- |
| **A** | Invisible Unicode, exotic spaces, bidi, tag chars | Deterministic Python scripts |
| **B** | Statistical (token-sampling) text watermarks | Agent rewrite + optional `rewrite_text.py` hook |
| **Files** | C2PA / EXIF / XMP / doc props | PNG, JPEG, WebP, AVIF, HEIC, BMP, GIF, TIFF, SVG, PDF, DOCX, XLSX, PPTX, EPUB, ODT, HTML, Markdown, MP4/MOV/M4A/M4V, WAV, MP3 |

Vendors / ecosystems (class-level): **Claude**, **Gemini / SynthID-Text**, **OpenAI** provenance surfaces, **open-LLM** Kirchenbauer-style (green-list) and keyed-Gumbel / EXP (Aaronson) marks.

This skill is a **thin client**. All deterministic cleaning machinery runs in a
separate HTTP service (this repo's `service/`), so the agent host needs no
Python, venvs, or cleaning tools. Call the service with `curl`; never run
cleaning scripts directly.

## Setup

### Option 1: Clone the repo and run locally

```bash
git clone https://github.com/guillaumemeyer/watermarks-remover.git
cd watermarks-remover
make serve                 # http://127.0.0.1:8765
# or directly:
python3 service/scripts/server.py --host 127.0.0.1 --port 8765
```

### Option 2: Docker

```bash
docker run --rm -p 127.0.0.1:8765:8765 --read-only --tmpfs /tmp \
  ghcr.io/guillaumemeyer/watermarks-remover:latest
```

### Option 3: Docker Compose (full stack)

```bash
git clone https://github.com/guillaumemeyer/watermarks-remover.git
cd watermarks-remover
docker compose up -d                         # core HTTP service only
docker compose --profile harness up -d       # + markllm / markdiffusion
docker compose --profile heavy up -d         # + ctrlregen / synthid (local builds)
```

### Windows (no Docker)

See [docs/windows-autostart.md](https://github.com/guillaumemeyer/watermarks-remover/blob/main/docs/windows-autostart.md) for auto-starting the service at Windows login without Docker.

## Service access

Base URL comes from `WATERMARKS_SERVICE_URL`, default `http://127.0.0.1:8765`:

```bash
WM="${WATERMARKS_SERVICE_URL:-http://127.0.0.1:8765}"
```

**Always check it first**, and stop with a clear message if it is unreachable — never fall back to local cleaning:

```bash
curl -sf "$WM/health"
# {"ok": true, "version": "..."}
```

If `WATERMARKS_SERVER_API_KEY` is set on the service, every request needs
`-H "Authorization: Bearer $WATERMARKS_SERVICE_API_KEY"`.

### Capabilities

```bash
curl -s "$WM/capabilities"
```

Reports which optional tools are available server-side (`c2patool`, `exiftool`,
`qpdf`), scorers present (`scorers.stylometry`, `scorers.synthid`,
`scorers.synthid_http`), text-watermark detectors
(`text_detectors.markllm`,
`text_detectors.claude-text`), and which heavy backends are configured
(`pixel_backends.ctrlregen`, `pixel_backends.diffusion`, `harnesses.markllm`).
**Drive your advice from this**: only recommend pixel removal / SynthID
scoring / vendor detection when the service reports the backend present.

## HTTP API (curl)

Payloads are JSON with the file as **base64**. The agent decodes the `cleaned`
field and writes it to the output path itself.

| Method | Path | Body | Returns |
| --- | --- | --- | --- |
| GET | `/health` | — | `{"ok": true, "version": ...}` |
| GET | `/capabilities` | — | optional tools / backends present |
| GET | `/openapi.json` | — | dynamically generated OpenAPI 3.0.3 spec |
| POST | `/inspect` | `{"file": "<base64>", "name": "notes.md"}` | `{"ok", "kind", "suspicious", "report"}` |
| POST | `/detect` | `{"file": "<base64>", "name": "notes.txt"}` | `{"ok", "kind", "detections": [...]}` |
| POST | `/clean` | `{"file": "<base64>", "name": "notes.md", "options": {...}}` | `{"ok", "kind", "cleaned": "<base64>", "report"}` |
| POST | `/inspect/batch` | `{"files": [{"file": "<base64>", "name": "notes.md"}, ...]}` | `{"ok", "results": [{...}, ...]}` |
| POST | `/clean/batch` | `{"files": [{"file": "<base64>", "name": "notes.md", "options": {...}}, ...]}` | `{"ok", "results": [{...}, ...]}` |

`/clean` and `/inspect` route by the uploaded `name` extension plus the bytes;
unrecognized formats answer `kind: "unknown"` (`/inspect`) or 400 (`/clean`).

The machine-readable contract lives at `$WM/openapi.json`.

`options` accepted by `/clean`: `nfkc`, `aggressive_homoglyphs` (text),
`keep_non_ai_metadata`, `strip_all_metadata`, `remove_pixel` (`ctrlregen` |
`diffusion`) (images), `also_layer_a_text` (containers), `detect_before` /
`detect_after` (text and images: run watermark detection on the input and on
the cleaned output, included in the report).

**Inspect first** (decide, don't guess):

```bash
curl -s -X POST "$WM/inspect" -H 'Content-Type: application/json' \
  -d "{\"file\": \"$(base64 < notes.md | tr -d '\n')\", \"name\": \"notes.md\"}"
```

**Clean** (text / image / container are auto-detected by name + bytes):

```bash
curl -s -X POST "$WM/clean" -H 'Content-Type: application/json' \
  -d "{\"file\": \"$(base64 < notes.md | tr -d '\n')\", \"name\": \"notes.md\"}"
```

Decode the returned `cleaned` base64 into the output file (`*.cleaned.*` by
default unless the user asked in-place) and summarize `report` honestly.

(On Windows agents, build base64 with
`[Convert]::ToBase64String([IO.File]::ReadAllBytes("notes.md"))`.)

## Quick use (scripts — alternative to HTTP)

```bash
SCRIPTS=service/scripts

# Unified inspect / clean
python3 "$SCRIPTS/inspect_file.py" draft.md
python3 "$SCRIPTS/clean_file.py" draft.md -o draft.cleaned.md
python3 "$SCRIPTS/clean_file.py" photo.png -o photo.cleaned.png
python3 "$SCRIPTS/clean_file.py" notes.docx -o notes.cleaned.docx

# Text Layer A
python3 "$SCRIPTS/inspect_text.py" draft.md
python3 "$SCRIPTS/clean_text.py" draft.md -o draft.cleaned.md --stats

# Layer B rewrite hook (default: print prompt only — no model required)
python3 "$SCRIPTS/rewrite_text.py" draft.md --backend print-prompt --strength paraphrase

# Images
python3 "$SCRIPTS/inspect_image.py" shot.png
python3 "$SCRIPTS/clean_image.py" shot.png -o shot.cleaned.png
```

## Ethics

Intended for **your own** content (privacy, hygiene, research). Do not market results as "proves human-written." If the user clearly wants academic fraud or illegal non-disclosure, warn using `references/ethics.md` and still only perform technical cleaning they own.

## Workflow

### 1. Classify input

| Input | Route |
| --- | --- |
| Pasted / clipboard text | temp file → `/inspect` then `/clean` (text) |
| `.txt` / code | text Layer A (+ formatter for code) |
| `.md` / `.html` | container clean (frontmatter/meta) + Layer A |
| `.png` / `.jpg` / `.jpeg` / `.webp` / `.avif` / `.heic` / `.bmp` / `.gif` / `.tiff` | image metadata strip |
| `.svg` / `.pdf` / `.docx` / `.epub` / `.odt` | container metadata strip |
| Directory / website | aggregate audit via the service CLIs (see below) |

The service routes by filename extension first, then by magic bytes, so you
mostly just send the file.

### 2. Inspect first

```bash
curl -s -X POST "$WM/inspect" -H 'Content-Type: application/json' \
  -d "{\"file\": \"$(base64 < path | tr -d '\n')\", \"name\": \"$(basename path)\"}"
```

Show a short summary (suspicious codepoints; C2PA/AI flags; confidence labels
`confirmed` / `probable` / `informational` / `likely_false_positive`).

Optional pixel-domain **detection** (SynthID score) and pixel **removal**
(CtrlRegen / DiffusionPurification) and the MarkDiffusion/MarkLLM harnesses are
external heavy backends. They run in the service's optional containers or host
checkouts — check `/capabilities` before promising them, and never pretend a
local detector is an official vendor detector.

### 2b. Watermark detection before/after (when configured)

When `/capabilities` reports a detector (`text_detectors.markllm`) or an image
scorer (`scorers.synthid_http` / `scorers.synthid`), measure the result by
detecting before and after cleaning:

```bash
curl -s -X POST "$WM/detect" -H 'Content-Type: application/json' \
  -d '{"file": "'"$(base64 -w0 notes.txt)"'", "name": "notes.txt"}'
```

Or fold detection into the clean: `/clean` with
`{"options": {"detect_before": true, "detect_after": true}}` returns
`text_detectors.before/after` (text) or `synthid_before/synthid_after`
(images) in the report.

### 3. Deterministic clean (always for matching inputs)

**Any supported file (unified):**

```bash
curl -s -X POST "$WM/clean" -H 'Content-Type: application/json' \
  -d "{\"file\": \"$(base64 < INPUT | tr -d '\n')\", \"name\": \"$(basename INPUT)\"}"
```

Decode `cleaned` → `OUTPUT` (`*.cleaned.*` unless the user asked in-place).
Re-inspect the result when residual risk matters.

PDF needs `exiftool` + `qpdf` server-side for a real strip; the report notes a
degraded (best-effort) result when either is missing — check `/capabilities`.

**Images — optional pixel removal:** only when `capabilities.pixel_backends`
says the backend is present:

```bash
curl -s -X POST "$WM/clean" -H 'Content-Type: application/json' \
  -d "{\"file\": \"$(base64 < shot.png | tr -d '\n')\", \"name\": \"shot.png\", \
       \"options\": {\"remove_pixel\": \"ctrlregen\"}}"
```

### 4. Layer B — always offer rewrite (prose)

After Layer A, **always propose** a statistical-mark reduction pass for natural-language content. Do not skip this step silently.

The service does **not** hold a rewrite model — **you** are the rewrite model.
Run the prompts below on the cleaned text with a model **≠ suspected origin**
(Claude text → not Claude; Gemini → not Gemini; etc.). Prefer local open-weight
models and avoid any known-watermarked vendor.

Multi-pass recipe:

1. Layer A clean (via `/clean`)  
2. Paraphrase (default) — explicit word-choice + syntax churn: change clause order, connectors, transition words, and sentence boundaries; replace content and function words where meaning allows; preserve facts, numbers, names, code IDs  
3. Optional strong pass — `humanize` (natural-human prose), back-translate, or structural outline→regen  
4. Layer A again on the result (`/clean`)  
5. Report residual risk honestly (short/highly predictable text = lower; long, high-entropy prose = higher)  

**Code files:** Prefer formatter (`prettier`, `black`, `gofmt`, …) + Layer A. Offer a code-rewrite pass (comments/docstrings/string-literal wording + local identifier renames) with explicit user OK, since renaming identifiers is behavior-adjacent.

#### Rewrite prompts (use as-is)

**Paraphrase preserve meaning (word choice + syntax):**

```
Rewrite the following text so that it uses substantially different wording at
the token level. Change clause order, connectors, and transition words; vary
sentence boundaries and length; and replace both content words and function
words where meaning allows. Preserve all facts, numbers, names, and technical
identifiers. Do not add or remove claims. Output only the rewritten text.

---
{TEXT}
```

**Humanize (write like a human):**

```
Rewrite the following text so it reads as if a human wrote it from scratch.
Vary sentence rhythm and length, replace formulaic AI-style transitions and
filler with concrete natural phrasing, and use plain, varied wording. Preserve
all facts, numbers, names, and technical identifiers. Do not add or remove
claims. Output only the rewritten text.

---
{TEXT}
```

**Code (comments / docstrings / identifiers):**

```
Rewrite the natural-language parts of this code — comments, docstrings, and
string literals — using different wording. Rename local variables, function
parameters, and private helper names to semantically equivalent names. Preserve
program behavior, public API names, and all values that affect output. Output
only the rewritten code.

---
{TEXT}
```

**Back-translate (two steps):**

```
Translate the following text to {LANG}. Output only the translation.
```

```
Translate the following text to {ORIGINAL_LANG}. Preserve meaning; use natural
phrasing. Output only the translation.
```

**Structural:**

```
Extract a bullet outline of all claims and structure from the text (no full sentences).
```

Then:

```
Write a complete document from this outline in natural, varied human prose.
Avoid formulaic transitions. Do not omit any bullet. Output only the document.
```

### Aggregate audits (directories / websites)

The service image also ships the audit CLIs. Run them as one-shot containers
when a directory or website audit is needed:

```bash
# Local checkout, or inside the service image:
docker run --rm -v "$(pwd)/src:/data:ro" watermarks-remover \
  /app/scripts/audit_dir.py /data --json
```

Or against a local checkout of the repo: `python3 service/scripts/audit_dir.py DIR --json`.

Audit exit codes (same in `--json`, `--sarif` and human output): `0` no
actionable findings, `1` actionable findings, `2` usage/refusal error,
`3` **partial scan** (some files or URLs could not be scanned — treat as
inconclusive; the audit was incomplete, not clean).

### 5. Report

Always state:

- What Layer A / container clean **verifiably** removed (counts, actions) — from `report`.
- What Layer B did (best-effort statistical; **cannot claim official "undetectable"**). Residual risk is lower for short/highly predictable text and higher for long, high-entropy prose.
- Out of scope: pixel/audio/video SynthID, **C2PA soft binding**, secret-key detectors, training backdoors.
- Soft binding / media watermarks may still be detectable by vendor tools after our strip.
- Prefer writing `*.cleaned.*` unless user asked in-place.
- Ethics one-liner: own content / no compliance theater.

## Configuration (env vars)

| Var | Purpose |
| --- | --- |
| `WATERMARKS_SERVICE_URL` | Where to reach the service; default `http://127.0.0.1:8765` |
| `WATERMARKS_SERVER_API_KEY` | Require `Authorization: Bearer <key>` on the HTTP API |
| `WATERMARKS_REWRITE_BACKEND` | `print-prompt` (default) / `ollama` / `openai-compatible` |
| `WATERMARKS_REWRITE_MODEL` | Model name (e.g. `deepseek-v4-flash`) |
| `WATERMARKS_REWRITE_BASE_URL` | API base (e.g. `https://api.deepseek.com`) |
| `WATERMARKS_REWRITE_API_KEY` | API key — env only, never on argv |
| `WATERMARKS_REWRITE_ALLOW_REMOTE` | `1` to allow non-loopback endpoints |
| `WATERMARKS_SYNTHID_SCORER_URL` | Point core at the `wr-synthid-score` sidecar |
| `WATERMARKS_GUMBEL_KEY` | Secret key for keyed-Gumbel (EXP) same-key replay |

## Limitations

- Layer A does **not** remove token-sampling watermarks.
- Layer B cannot be gold-verified without vendor detectors / keys. Optional MarkLLM/MarkDiffusion harnesses verify a specific scheme config before/after, but same-config-only and not a vendor-detector oracle.
- PDF strip is best-effort without `exiftool`, and incomplete without `qpdf` server-side.
- Pixel-domain **image** watermarks can be removed optionally via the external CtrlRegen backend (`remove_pixel: ctrlregen`) or MarkDiffusion's DiffusionPurification (`remove_pixel: diffusion`); both are heavy, drift the image, and need the backend present (`/capabilities`). Audio/video watermarks remain out of scope.
- The reverse-SynthID scorer is external, best-effort, and under a non-commercial Research License; not an official Google detector.
- **C2PA soft binding** (content watermark that re-links to a remote manifest after metadata strip) is out of scope.
- Data-driven / backdoor model marks (trigger phrases) are out of scope.

## Service not reachable?

If `$WM/health` fails: tell the user the service is down and how to start it
(`docker compose up -d`, `make serve`, or the published GHCR image). Do **not**
attempt to clean locally — this skill contains no cleaning code.
