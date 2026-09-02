---
type: source
status: ingested
title: "EAGLE-3: Scaling up Inference Acceleration of Large Language Models via Training-Time Test"
arxiv: 2503.01840
year: 2025
authors: [Yuhui Li, Fangyun Wei, Chao Zhang, Hongyang Zhang]
venue: NeurIPS (arxiv)
pdf: raw/papers/2503.01840_eagle3.pdf
txt: raw/papers/txt/2503.01840_eagle3.txt
tags: [llm, eagle]
related: [eagle-3, training-time-test, eagle-2]
updated: 2026-09-02
---

# Summary — EAGLE-3

## Problem

LLM intelligence scaled with **data** at fixed inference cost (LLaMA 1→3). EAGLE draft models **do not**: extra ShareGPT-scale data barely moves speedup. Cause: **feature-prediction loss** is a bottleneck. Removing it raises 0-step accept but self-generated features at step 2 leave the train distribution → 1-step accept collapses.

## Method

**Training-time test:** unroll the draft during training so step-2 inputs are the model's own step-1 outputs. Then you can drop `l_fea` and predict **tokens** directly.

That also frees the input: instead of only top-layer (next-token) features, **fuse low / mid / high** target hidden states. Top-layer features are informationally tied to *next*-token logits (full-rank LM head); they are a bad sufficient statistic for token t+2.

Keeps EAGLE-2's [[dynamic-draft-tree]]. Paper notes EAGLE influenced DeepSeek-V3 multi-token prediction, which fed back into this design.

## Results to keep

- Speedup **up to 6.5×**; **~1.4× over EAGLE-2**.
- Chat + reasoning models (incl. DeepSeek-R1-Distill-LLaMA 8B), five tasks.
- SGLang, batch 64: **+1.38× throughput** (counters "specdec only helps BS=1").
- ~8× more draft training data than EAGLE-1. Scaling curve vs data appears (Fig. 1); EAGLE-2's curve is flat-ish.

## What it changes here

Defines [[eagle-3]] and [[training-time-test]]. [[p-eagle]] starts from this stack and parallelizes the drafter. ViSpec cites EAGLE-3 MTP but says gains need data scale.
