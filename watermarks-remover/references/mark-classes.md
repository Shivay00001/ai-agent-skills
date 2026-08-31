# Mark classes

## 1. Edit-based text (Unicode / rules)

Invisible or near-invisible characters, exotic spaces, bidi controls, tag characters, synonym tables.

| Inspect kinds (Layer A) | Examples |
| --- | --- |
| `zwj_family` | ZWSP, ZWNJ, ZWJ, WJ, BOM |
| `bidi` | LRE/RLO/LRI/… |
| `tag_chars` | U+E0001–U+E007F |
| `variation_selector` | VS1–VS256 |
| `private_use` | U+E000–F8FF, U+F0000–FFFFD, U+100000–10FFFD |
| `noncharacter` | U+FDD0–FDEF, U+FFFE/U+FFFF at the end of every plane |
| `reserved_ignorable` | U+2065, U+FFF0–FFF8, U+E0000, U+E0080–E00FF, U+E01F0–E0FFF (unassigned Default_Ignorable) |
| `space` | NBSP, em space, ideographic space |
| `confusable` | Cyrillic/fullwidth Latin (aggressive) |

**Removal:** `clean_text.py` / Layer A — deterministic, verifiable.

Load-bearing invisibles are preserved by default so real text is not corrupted: emoji glue (ZWJ/VS after an emoji base), script joiners (ZWNJ/ZWJ inside complex scripts like Persian or Devanagari), flag tag-char sequences, same-script fillers/selectors (Mongolian free variation selectors after a Mongolian letter, Khmer inherent vowels after a Khmer consonant, Hangul jamo fillers in a partial syllable), orthographic Arabic/Syriac `Cf` marks, and visible-layout format controls next to their own script. The same characters between plain ASCII stay carriers and are still stripped. Use `--strip-emoji-glue` for paranoid mode.

Maps to Nature paper "edit-based watermarking."

## 2. Generative / statistical text (token sampling)

Bias next-token sampling toward a pseudo-random green list / score (Kirchenbauer, SynthID-Text / Tournament sampling, etc.). Signal lives in **word choice**, not metadata.

**Removal:** Layer B rewrite (paraphrase → back-translate → structural). Best-effort; no gold cert without vendor detector/key.

Maps to Nature paper primary method (SynthID-Text).

## 3. Document / container metadata (C2PA, EXIF, XMP, doc props)

Structured metadata fields in file containers: C2PA manifests (signed provenance), EXIF/XMP/IPTC (camera/tool metadata), document properties (OOXML core/app/custom), ODF `meta.xml`, HTML `<meta>` tags, SVG `<metadata>`.

**Removal:** Container-specific stripping — deterministic, verifiable.

## 4. Pixel-domain image watermarks

Imperceptible perturbations in pixel data (SynthID-media, StegaStamp, Tree-Ring, StableSignature). Survives metadata strip, screenshot, re-encoding.

**Removal:** Optional external backends (CtrlRegen, DiffusionPurification). Heavy, drifts image. Out of scope without the backend.

## 5. Data-driven / backdoor marks

Trigger phrases or training-time patterns. **Out of scope** — cannot be detected or removed without model internals.
