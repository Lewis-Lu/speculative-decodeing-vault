---
type: source
status: ingested
title: "SpecVLM: Fast Speculative Decoding in Vision-Language Models"
arxiv: 2509.11815
year: 2025
authors: [Haiduo Huang, Fuwei Yang, Zhenhua Liu, Xuanwu Yin, Dong Li, Pengju Ren, Emad Barsoum]
venue: arXiv
pdf: raw/papers/2509.11815_specvlm.pdf
txt: raw/papers/txt/2509.11815_specvlm.txt
tags: [vlm, eagle]
related: [specvlm, eaglevlm, visual-token-bottleneck, online-logit-distillation]
updated: 2026-09-02
---

# Summary — SpecVLM

AMD + Xi'an Jiaotong. First-class **systems** paper for VLM specdec on the EAGLE-2 stack.

## Problem

VLM prefill is vision-token dominated (resolution / video). KV cache blows up. Naive specdec still pays a huge draft prefill.

LLaVA-1.6-7B latency breakdown (BS=1, T=0, RTX 4090, paper Fig. 1): LLM **prefill** is the main non-encoder cost; decode is the second bottleneck.

## Method (three parts)

1. **EagleVLM** — EAGLE-2-style baseline on VLMs: **1.5–2.3×** E2E vs full AR.
2. **Elastic visual compressor** — pick among pruning / pooling / conv / resampler per input to trade FLOPs vs accuracy on the **draft** path.
3. **[[online-logit-distillation]]** — train draft on on-the-fly teacher logits + penultimate features (CE + Smooth L1). No offline distillation dump. Longer online training → higher average accepted length (monotonic in paper).

Lossless on the target distribution.

## Results to keep

- SpecVLM: **2.5–2.9×** E2E within **5 epochs**, LLaVA + MMMU, across resolutions / difficulty.
- Fig. 1b LLaVA-Bench-in-the-Wild: EagleVLM ~1.9–2.3×, SpecVLM ~2.0–2.4× on the 7B/13B v1.5/v1.6 set (paper bars).

Code: [haiduo/SpecVLM](https://github.com/haiduo/SpecVLM).

## What it changes here

Defines [[specvlm]], [[eaglevlm]], [[visual-token-bottleneck]], [[online-logit-distillation]]. Contrast [[vispec]] (different bottleneck: draft cannot filter images).
