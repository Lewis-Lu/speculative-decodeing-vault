---
type: source
status: ingested
title: "SpecInfer: Accelerating Generative Large Language Model Serving with Tree-based Speculative Inference and Verification"
arxiv: 2305.09781
year: 2024
authors: [Xupeng Miao, Gabriele Oliaro, Zhihao Zhang, Xinhao Cheng, and others]
venue: ASPLOS 2024
pdf: raw/papers/2305.09781_specinfer.pdf
txt: raw/papers/txt/2305.09781_specinfer.txt
tags: [llm, tree, serving]
related: [tree-attention, specinfer, speculative-decoding]
updated: 2026-09-02
---

# Summary — SpecInfer

Serving system, not a new sampling identity. Organizes small-model guesses as a **token tree**; the LLM verifies **all** branches in one tree-attention forward. Target is a verifier, not a token-at-a-time decoder.

## Results to keep

- Distributed serving: **1.5–2.8×** vs existing systems.
- Offloading serving: **2.6–3.5×**.
- Quality preserved.

## What it changes here

EAGLE's tree drafts and [[tree-attention]] sit in this line (also Medusa). Chain drafts discard the suffix on first reject; trees keep sibling prefixes. Code: [flexflow/FlexFlow](https://github.com/flexflow/FlexFlow/).
