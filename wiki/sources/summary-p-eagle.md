---
type: source
status: ingested
title: "P-EAGLE: Parallel-Drafting EAGLE with Scalable Training"
arxiv: 2602.01469
year: 2026
authors: [Mude Hui, Xin Huang, Jaime Campos Salas, Yue Sun, Nathan Pemberton, Xiang Song, Ashish Khetan, George Karypis]
venue: arXiv (AWS)
pdf: raw/papers/2602.01469_p_eagle.pdf
txt: raw/papers/txt/2602.01469_p_eagle.txt
tags: [llm, eagle, parallel-draft]
related: [p-eagle, eagle-3]
updated: 2026-09-02
---

# Summary — P-EAGLE

AWS. EAGLE-3 still **autoregresses** the drafter: K draft tokens ⇒ K serial drafter forwards. Bad when generations are long (reasoning).

GPT-OSS 120B on UltraChat: median seq **3,891**, P90 **10,800**. Drafters trained short drop ~**25%** accept rate on long traces.

## Method

- Parallel multi-token prediction with a **learnable shared hidden state** (placeholders for positions 2…K).
- Training: attention-mask precompute + **sequence partitioning** so memory does not scale as (seq_len × parallel_depth)².
- vLLM implementation.

Vs ParallelSpec (OOM / weak AL at long ctx) and PARD (infeasible masks past ~4k). P-EAGLE trains to **20k** ctx; AL on MT-bench / GPT-OSS 120B, spec length 5: **2.4 → 3.0** as ctx 1k→20k.

## Results to keep

- **1.10–1.36×** over autoregressive **EAGLE-3** on GPT-OSS 120B, 20B, Qwen3-Coder 30B (not vs vanilla AR).

## What it changes here

Defines [[p-eagle]]. Next serial bottleneck after EAGLE-3 acceptance is high.
