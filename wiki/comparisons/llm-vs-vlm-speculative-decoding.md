---
type: comparison
status: active
sources: [summary-eagle, summary-specvlm, summary-vispec]
updated: 2026-09-02
---

# LLM vs VLM speculative decoding

## What transfers

- [[draft-and-verify]] identity still holds: outputs are text tokens.
- EAGLE-2 [[dynamic-draft-tree]] is the default tree policy in both SpecVLM and ViSpec.
- Feature / hidden-state injection is still the way a 1-layer drafter "cheats" up to target quality.

## What does not

| LLM specdec | VLM specdec |
|---|---|
| Prefill is prompt tokens | Prefill often **dominated by visual tokens** ([[visual-token-bottleneck]]) |
| Small sibling LM or 1-layer text drafter | 1-layer drafter **cannot filter images** (ViSpec); also **cannot afford full visual KV** (SpecVLM) |
| ShareGPT-scale text is enough to start | VQA answers too short; need long synthetic traces (ViSpec) or online distillation (SpecVLM) |
| Headline 3–6× | EagleVLM only **1.5–2.3×**; extra systems work to reach ~2.5–3× |

Do not quote LLaMA-70B EAGLE numbers as VLM expectations.
