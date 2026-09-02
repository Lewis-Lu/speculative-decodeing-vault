---
type: source
status: ingested
title: "Hydra: Sequentially-Dependent Draft Heads for Medusa Decoding"
arxiv: 2402.05109
year: 2024
authors: [Zachary Ankner, Rishab Parthasarathy, Aniruddha Nrusimha, Christopher Rinard, Jonathan Ragan-Kelley, William Brandon]
venue: arXiv
pdf: raw/papers/2402.05109_hydra.pdf
txt: raw/papers/txt/2402.05109_hydra.txt
tags: [llm, heads]
related: [hydra, medusa]
updated: 2026-09-02
---

# Summary — Hydra

Medusa heads are **sequentially independent** (each offset ignores previously speculated tokens). Hydra heads condition on the prefix of the candidate continuation. Hydra++ is a tuned recipe.

## Results to keep

- Up to **1.31×** vs Medusa throughput.
- Up to **2.70×** vs vanilla AR.

## What it changes here

Evidence that **dependence along the draft** (which EAGLE gets "for free" via AR + shifted token) is the missing piece in pure parallel heads. Code: [zankner/Hydra](https://github.com/zankner/Hydra).
