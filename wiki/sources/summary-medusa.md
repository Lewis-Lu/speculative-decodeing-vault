---
type: source
status: ingested
title: "Medusa: Simple LLM Inference Acceleration Framework with Multiple Decoding Heads"
arxiv: 2401.10774
year: 2024
authors: [Tianle Cai, Yuhong Li, Zhengyang Geng, Hongwu Peng, Jason D. Lee, Deming Chen, Tri Dao]
venue: arXiv
pdf: raw/papers/2401.10774_medusa.pdf
txt: raw/papers/txt/2401.10774_medusa.txt
tags: [llm, heads]
related: [medusa, tree-attention, hydra]
updated: 2026-09-02
---

# Summary — Medusa

Princeton / Together et al. Extra **decoding heads** on the target residual stream predict tokens at offsets +1…+K **independently**. Tree attention + acceptance. No separate draft LM.

## Variants

- **Medusa-1:** freeze backbone, train heads only → lossless if you use standard verify.
- **Medusa-2:** train heads **with** backbone (special recipe to keep quality) → higher speedup, not a frozen-target method.
- Self-distillation when no corpus; **typical acceptance** to raise accept rate (quality recipe, not Leviathan-identity).

## Results to keep

- Medusa-1: **>2.2×** without compromising generation quality (paper claim).
- Medusa-2: **2.3–3.6×**.

EAGLE's critique: independent heads ignore sequential dependence and inherit feature uncertainty; draft accuracy ~0.6. [[hydra]] adds sequential dependence on the same head idea.

## What it changes here

Primary contrast class for [[eagle-vs-medusa]]. Code: [FasterDecoding/Medusa](https://github.com/FasterDecoding/Medusa/).
