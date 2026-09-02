---
type: source
status: ingested
title: Break the Sequential Dependency of LLM Inference Using Lookahead Decoding
arxiv: 2402.02057
year: 2024
authors: [Yichao Fu, Peter Bailis, Ion Stoica, Hao Zhang]
venue: arXiv
pdf: raw/papers/2402.02057_lookahead.pdf
txt: raw/papers/txt/2402.02057_lookahead.txt
tags: [llm, jacobi]
related: [lookahead-decoding]
updated: 2026-09-02
---

# Summary — Lookahead Decoding

No auxiliary draft model and no extra datastore. Jacobi-style parallel n-gram guesses from the **same** LLM, verified exactly. Trades extra FLOPs per step for fewer serial steps. FlashAttention-compatible.

## Results to keep

- Up to **1.8×** on MT-bench.
- Up to **4×** with multi-GPU strong scaling on code completion.

Greedy-oriented in comparisons used by EAGLE (EAGLE plots often exclude Lookahead at T=1). Lower draft accuracy than EAGLE/Medusa in EAGLE's telling.

## What it changes here

Shows a third cluster: **self-draft without a trained head**. Code: [hao-ai-lab/LookaheadDecoding](https://github.com/hao-ai-lab/LookaheadDecoding).
