# How Claude marks AI-generated content

Primary source: [Anthropic Help Center](https://support.claude.com/en/articles/16266773-how-claude-marks-ai-generated-content) (EU AI Act Article 50(2) Code of Practice).

## Policy snapshot

| Topic | Anthropic position |
| --- | --- |
| New models | Marking for models launched on/after **2026-08-02** |
| Older models | Transition; "in progress" |
| Surfaces | API, Claude, Claude Code, Cowork, Tag |
| Regions | **Worldwide** |
| Detection | Third-party detection promised; docs **forthcoming** |

## Mechanism 1 — embedded text watermarks

- Applied at the **model level** into the text itself (not file metadata).
- Imperceptible; survives copy-paste; may survive light editing.
- Weakened by paraphrase, translation, heavy edit, mixing, short text.

**Likely technical class** (Anthropic has not published the algorithm): statistical **token-sampling** watermarks (Kirchenbauer / SynthID-style). See `vendor-notes.md` and `mark-classes.md`.

Layer A (Unicode hygiene) does not target this; Layer B (rewrite) does.

## Mechanism 2 — C2PA Content Credentials

- On supported file types (images, SVG, PDF, etc.)
- Signed metadata asserting "processed by Claude"
- Stripped by the service's container/image cleaning pipeline

## Caveats (Anthropic's own)

- Mark ⇒ may have been processed by Claude
- No mark ≠ human-only
- Proofreading can stamp human text
