# Removal matrix

| Target | Method | Script / action | Side effects | Verifiable today? |
| --- | --- | --- | --- | --- |
| Invisible Unicode / exotic spaces / bidi / tags | Strip / normalize | `inspect_text.py`, `clean_text.py`, `clean_file.py` | Minimal | Yes (codepoint report) |
| Stylometric AI cadence / burstiness / n-grams (zero-LLM) | Statistical variance & cadence scoring | `score_stylometry.py`, `inspect_text.py --stylometry`, `audit_dir.py --check-stylometry` | None (detection only) | Yes (calibrated score + phrase spans) |
| Statistical text watermark (SynthID-class / Kirchenbauer) | Multi-pass paraphrase / humanize / back-translate / structural | Agent Layer B + optional `rewrite_text.py` | Meaning/style drift | No without vendor key/detector; **MarkLLM harness** (`detect_text_watermark.py`) verifies a specific scheme config before/after |
| C2PA on PNG/JPEG/WebP/AVIF/HEIC | Drop APP11 / PNG `caBX` / RIFF `C2PA` / ISOBMFF `jumb` & `uuid` / exiftool | `clean_image.py` | Loses provenance metadata | Yes |
| GIF comment/XMP extensions | Drop 0xFE / XMP application extensions (keep `NETSCAPE2.0`) | `clean_image.py` | Loses GIF comments/XMP | Yes (re-inspect) |
| TIFF XMP/EXIF/GPS/IPTC/MakerNote (classic + BigTIFF) | Drop IFD tags, zero payloads, keep strip offsets | `clean_image.py` | Loses TIFF metadata | Yes (re-inspect) |
| BMP trailing metadata | Truncate non-image trailing bytes, fix file-size field | `clean_image.py` | Removes appended metadata | Yes (re-inspect) |
| EPUB OPF metadata / XHTML meta / embedded media | Scrub OPF, strip XHTML meta/JSON-LD, clean embedded media, Layer A (skip encrypted parts) | `clean_file.py` | Loses book metadata; rewrites archive | Yes (re-inspect) |
| SVG metadata / XMP / embedded data URIs | Drop `<metadata>`, xmpmeta; clean embedded data URIs | `clean_file.py` | Loses SVG metadata; cleans embedded rasters | Yes (re-inspect) |
| PDF XMP / info | exiftool `-all=` preferred | `clean_file.py` | Loses PDF metadata; degraded without exiftool | Partial |
| DOCX / XLSX / PPTX props / customXml / embedded media | Rewrite OOXML zip, scrub text runs, clean media/ | `clean_file.py` | Loses doc properties; cleans embedded rasters | Yes |
| ODT meta:generator | Scrub `meta.xml` | `clean_file.py` | Loses generator metadata | Yes |
| HTML meta tags / JSON-LD / embedded media | Strip AI meta, schema.org, embedded data URIs, Layer A | `clean_file.py` | Loses HTML metadata | Yes |
| Markdown frontmatter / HTML meta / embedded images | Strip YAML frontmatter AI fields, HTML meta, clean embedded images | `clean_file.py` | Loses frontmatter metadata | Yes |
| MP4/MOV/M4A/M4V MPEG-4 containers | exiftool strip + C2PA jumb/uuid removal | `clean_file.py` | Loses video/audio metadata | Yes (re-inspect) |
| WAV RIFF containers | Strip non-essential chunks (LIST/INFO/ICMT/bext/iXML/axml/XMP) | `clean_file.py` | Loses audio metadata | Yes (re-inspect) |
| MP3 ID3/APE tags | Strip ID3v1, ID3v2, APEv2 tags | `clean_file.py` | Loses audio metadata tags | Yes (re-inspect) |
| Pixel-domain image watermarks (SynthID, StegaStamp, Tree-Ring, StableSignature) | CtrlRegen / DiffusionPurification (external) | `clean_image.py --remove-pixel ctrlregen` or `diffusion` | Image drift | Optional; external backend required |
