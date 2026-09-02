---
type: source
status: ingested
title: "EAGLE-2: Faster Inference of Language Models with Dynamic Draft Trees"
arxiv: 2406.16858
year: 2024
authors: [Yuhui Li, Fangyun Wei, Chao Zhang, Hongyang Zhang]
venue: EMNLP 2024
pdf: raw/papers/2406.16858_eagle2.pdf
txt: raw/papers/txt/2406.16858_eagle2.txt
tags: [llm, eagle]
related: [eagle-2, dynamic-draft-tree, acceptance-rate, eagle]
updated: 2026-09-02
---

# Summary — EAGLE-2

Same authors. **No new draft training.** Changes how the draft *tree is grown*.

## Observation

Static trees (EAGLE, Medusa, Sequoia-style position-only acceptance) assume accept rate ≈ f(depth, branch index). Empirically accept rate is also **context-dependent** (high variance at a given tree position on Alpaca / Vicuna-7B).

EAGLE's draft **confidence is calibrated**: p_draft ≈ P(accept). So you can expand high-value nodes and rerank before the target verify, without querying the target during drafting.

## Method

- **Expand:** feed the most promising frontier nodes into the draft model for the next layer.
- **Rerank / prune:** keep tokens with higher approximated accept probability as the verify set.

Still standard speculative sampling on the surviving tree → lossless.

## Results to keep

- **3.05–4.26×** speedup; **20–40% faster than EAGLE-1**.
- Vicuna, LLaMA2-Chat, LLaMA3-Instruct; six tasks (MT-bench, HumanEval, GSM8K, Alpaca, CNN/DM, NQ).
- vs Medusa ~2×, vs Lookahead ~2.3× on MT-bench (paper figures; lossless only comparators in the main plots).
- Claimed #1 on Spec-Bench at submission of EAGLE-1; EAGLE-2 keeps that stack.

## What it changes here

Defines [[eagle-2]] and [[dynamic-draft-tree]]. EAGLE-3 and SpecVLM/ViSpec reuse this tree policy.
