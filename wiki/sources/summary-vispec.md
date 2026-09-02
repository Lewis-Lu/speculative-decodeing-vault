---
type: source
status: ingested
title: "ViSpec: Accelerating Vision-Language Models with Vision-Aware Speculative Decoding"
arxiv: 2509.15235
year: 2025
authors: [Jialiang Kang, Han Shu, Wenshuo Li, Yingjie Zhai, Xinghao Chen]
venue: NeurIPS 2025
pdf: raw/papers/2509.15235_vispec.pdf
txt: raw/papers/txt/2509.15235_vispec.txt
tags: [vlm, eagle]
related: [vispec, vision-aware-drafting, eagle]
updated: 2026-09-02
---

# Summary — ViSpec

PKU / Huawei Noah. Hypothesis: **large VLMs filter redundant vision layer by layer; tiny drafters cannot.** Prior VLM specdec (language-only draft on LLaVA-7B) stalled at **<1.5×**.

Uses EAGLE-2 [[dynamic-draft-tree]].

## Method

1. **Vision adaptor** compresses image tokens; injects them into draft attention **keeping original image positions**.
2. **Global visual feature** (EAGLE-style target-aware injection) added to all following **text** tokens until the next image.
3. **Data:** VQA answers are too short. Repurpose datasets + target VLM with modified prompts to synthesize **long** assistant traces.
4. **Training:** multi-token prediction (DeepSeek-style); randomness + MTP to avoid **shortcut learning** from target hidden states.

## Results to keep

- Fig. 1 (T=0, GQA): ViSpec above vanilla / Medusa / EAGLE-2 on LLaVA-1.6 7B/13B and Qwen2.5-VL 3B/7B. Paper: "first substantial speedup" in VLM specdec.
- Search/secondary reports quote up to **~3.22×** — treat as non-canonical until pinned to a table in a later lint.

Code: [KangJialiang/ViSpec](https://github.com/KangJialiang/ViSpec).

## Tension

Concurrent with [[summary-specvlm]]. Different diagnosis (semantic redundancy vs token count / distillation). Do not equate headline speedups. See [[specvlm-vs-vispec]].
