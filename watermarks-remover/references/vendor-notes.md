# Vendor notes (public / class-level)

This skill targets **mark classes**, not reverse-engineered private detectors. Details below are from public docs and the research literature. Algorithms may change.

## Industry two-layer model (context)

Product and regulatory guidance often frames AI disclosure as:

1. **C2PA Content Credentials** — signed, hard-bound metadata (easy to strip; what this skill removes).
2. **Imperceptible watermark** (SynthID-class) — survives strip/re-upload; includes **soft binding** that can re-attach a remote C2PA manifest.

See: [Institute of AI PM — C2PA and SynthID guide](https://www.institutepm.com/knowledge-hub/ai-content-provenance-watermarking) (SB 942 / EU AI Act Art. 50 framing). This project only implements the **hard-bound / Unicode / rewrite** side of that stack.

## Anthropic / Claude

- **Embedded text watermarks** at model level (imperceptible; survive copy-paste). Public description matches **statistical token-sampling** class, not only Unicode.
- **C2PA Content Credentials** on supported files (e.g. PNG, JPEG, SVG).
- Models launched on/after **2026-08-02**: marking at launch; older models in transition; **worldwide**.
- Detection APIs for third parties: described as forthcoming.
- Caveats: mark ⇒ may have been processed by Claude; no mark ≠ human-only; proofreading can stamp human text.

**Skill mapping:** Layer A (Unicode hygiene) + Layer B (rewrite) + container/image C2PA strip.

Source: [How Claude marks AI-generated content](https://support.claude.com/en/articles/16266773-how-claude-marks-ai-generated-content).

## Google Gemini / SynthID-Text

- Nature 2024 paper: *Scalable watermarking for identifying large language model outputs* (SynthID-Text).
- **Generative watermarking**: modifies next-token sampling (Tournament sampling); detection uses a scoring function + key; no need for the LLM at detect time.
- Paper also taxonomizes:
  - **Edit-based** (Unicode / synonym rules) → our Layer A (+ Layer B for synonyms)
  - **Data-driven / backdoor** (trigger phrases) → **out of scope**
  - **Generative** (sampling) → Layer B best-effort
- Productionized in Gemini-scale systems; open research code exists, but **production keys are not public** — this skill does **not** ship a SynthID detector.
- **Retired from the API (Aug 2026):** Google confirmed the Generative Language API no longer watermarks text output and DETECT_TEXT_WATERMARK is rejected on current (3.x) models; "native text watermarking is not planned at the moment" ([Google AI forum](https://discuss.ai.google.dev/t/does-gemini-api-text-output-carry-synthid-watermarking-gemini-2-5-flash-lite-gemini-3-1-flash-lite-eu-ai-act-art-50-2/177241/2)). The gemini-synthid-text detector was **removed** for this reason; a vendor detector can be re-added if Google exposes detection again.

**Skill mapping:** Layer B (rewrite) + any C2PA on Gemini-generated images.

## OpenAI

- **C2PA Content Credentials** on DALL-E and other image outputs.
- **Text**: no public watermarking (internal research paused/unreleased as of 2024).
- Possible future metadata marking on API outputs (no details public).

**Skill mapping:** Container/image C2PA strip. No Layer B needed for text (no watermark announced).

## Open-LLM / Kirchenbauer-class

- Research implementations: Kirchenbauer green-list (KGW), Aaronson keyed-Gumbel (EXP), others.
- Used by self-hosted / open-weight deployments that opt into watermarking.
- Detection requires the same key/config.

**Skill mapping:** Layer B (rewrite). MarkLLM harness can verify a specific scheme before/after.
