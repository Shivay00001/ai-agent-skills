# MarkDiffusion (THU-BPM) — reference

External research backend: [`THU-BPM/MarkDiffusion`](https://github.com/THU-BPM/MarkDiffusion)
(JMLR; Apache-2.0). A **generative watermarking** toolkit for latent diffusion
models — it *embeds* marks, it does not remove them. This repo uses it as a
controlled-experiment harness and as an optional regeneration-removal engine.

## What it covers (image-only scope)

Nine image algorithms in two categories:

| Category | Algorithms | Notes |
| --- | --- | --- |
| Pattern-based | Tree-Ring, Ring-ID, ROBIN, WIND, SFW | A fixed latent/FT pattern is injected at generation and inverted for detection |
| Key-based | Gaussian-Shading, GaussMarker, PRC, SEAL | A secret key modulates the noise/latent; detection needs the key |

(Video algorithms VideoShield / VideoMark are out of scope for this project.)

## What it gives the remover

- **Same-scheme detector** for the above algorithms via `AutoWatermark.load(...).detect_watermark_in_media()`. Covers the Tree-Ring-class gap in
  `removal-matrix.md`; it does **not** cover StegaStamp, StableSignature, or
  SynthID-media.
- **`DiffusionPurification`** — a blind regeneration attack (DiffPure-style:
  encode → partial noise → reverse-denoise) usable as a pixel-watermark remover.
  Exposed as `--remove-pixel diffusion` in `clean_image.py`.
- **`NeuralCodecCompression`** — codec round-trip (compressai). Not wired here.

## Hard honesty constraints

1. **Detection is same-scheme and same-model only.** Inversion-based detection
   requires the generating model (and for key-based schemes the key). It proves
   "this image came from *this* model/config/params" — it cannot certify that a
   vendor detector will fail on an arbitrary image. This is the same
   same-config-only caveat as the MarkLLM text harness.
2. **`DiffusionPurification` is a blind attack** — it does not need the
   watermarking scheme or key, but it drifts the image. Higher noise = more
   removal but more visual change. Always report strength and visual impact.
3. **MarkDiffusion detection != vendor detection.** Never claim that passing a
   MarkDiffusion detector means an image is "unwatermarked" in the vendor sense.
