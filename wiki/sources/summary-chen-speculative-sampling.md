---
type: source
status: ingested
title: Accelerating Large Language Model Decoding with Speculative Sampling
arxiv: 2302.01318
year: 2023
authors: [Charlie Chen, Sebastian Borgeaud, Geoffrey Irving, Jean-Baptiste Lespiau, Laurent Sifre, John Jumper]
venue: arXiv
pdf: raw/papers/2302.01318_chen_speculative_sampling.pdf
txt: raw/papers/txt/2302.01318_chen_speculative_sampling.txt
tags: [llm, foundational]
related: [speculative-decoding, draft-and-verify, lossless-acceleration]
updated: 2026-09-02
---

# Summary — Chen et al. (speculative sampling)

DeepMind. Concurrent formulation; EAGLE papers usually cite **both** Leviathan and this one.

## Method

Draft length *K* from a faster AR model (or a parallel model). Target scores the draft. Modified **rejection sampling**:

- Accept draft token \(\hat{x}\) with \(\min(1, p(\hat{x})/\hat{p}(\hat{x}))\).
- On reject, sample from \(\mathrm{norm}(\max(0, p - \hat{p}))\) and drop the rest of the draft.

Preserves the target distribution within hardware numerics.

## Results to keep

- Chinchilla 70B, distributed setup: **2–2.5×** decoding speedup, no model surgery.

## What it changes here

Names the two roles **draft model** / **target model** used everywhere downstream. Same algorithm family as [[summary-leviathan-speculative-decoding]].
