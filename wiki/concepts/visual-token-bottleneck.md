---
type: concept
status: active
sources: [summary-specvlm]
updated: 2026-09-02
---

# Visual token bottleneck

In VLMs, token count from the vision encoder scales with resolution and video length. That inflates:

- vision encoder / projector time,
- **LLM prefill** (often the largest LLM-side bar on LLaVA-1.6-7B in SpecVLM Fig. 1),
- KV cache traffic on every decode step.

[[speculative-decoding]] only reduces **decode steps**. It does not shrink vision-encoder time. Draft models that still attend full visual sequences pay a prefill tax that can erase specdec gains. SpecVLM's elastic compressor attacks this; ViSpec compresses via a vision adaptor instead.
