---
type: source
status: ingested
title: "EAGLE: Speculative Sampling Requires Rethinking Feature Uncertainty"
arxiv: 2401.15077
year: 2024
authors: [Yuhui Li, Fangyun Wei, Chao Zhang, Hongyang Zhang]
venue: ICML 2024
pdf: raw/papers/2401.15077_eagle.pdf
txt: raw/papers/txt/2401.15077_eagle.txt
tags: [llm, eagle]
related: [eagle, feature-level-autoregression, feature-uncertainty, tree-attention]
updated: 2026-09-02
---

# Summary — EAGLE

Peking / MSR / Waterloo. Hub paper of this vault.

## Observations

1. Autoregression at the **feature** (second-to-top / pre-LM-head) layer is easier than at tokens. Then reuse the **target LM head**.
2. Feature AR is ill-posed under sampling: next feature depends on which token was drawn ([[feature-uncertainty]]). Medusa's parallel heads have the same ambiguity.

Fix: feed the draft model the **token sequence advanced by one step** (the sampling outcome) together with the feature sequence.

Draft model: **one Transformer decoder layer** (<1B even for a 70B target), trained on 2–4B tokens / ~70k ShareGPT dialogues — vs TinyLLaMA-scale pretraining.

Drafts are **trees**, verified with [[tree-attention]]. Target weights frozen → [[lossless-acceleration]] (greedy and sampling).

## Results to keep

- LLaMA2-Chat 70B: **2.7–3.5×** latency, ~2× throughput, distribution unchanged.
- Vicuna / LLaMA2-Chat / Mixtral 8x7B; MT-bench, HumanEval, GSM8K, Alpaca.
- Draft accuracy ~**0.8** vs Medusa ~**0.6**.
- vs Lookahead **1.7–2.1×**, vs Medusa **1.5–1.6×** (same paper's comparison on MT-bench).
- gpt-fast combo: LLaMA2-Chat 7B → **160.4 tok/s** on 1× RTX 3090.
- Ablation (Vicuna 7B, T=0, MT-bench): token AR 1.5× → feature AR 1.9× → feature+shifted-token **2.8×**.

Vanilla specdec is often N/A for 7B (no cheaper sibling) or slow if 7B drafts 13B.

## What it changes here

Defines [[eagle]], [[feature-level-autoregression]], [[feature-uncertainty]]. Later: [[eagle-2]], [[eagle-3]]. Authors: [[yuhui-li]]. Code: [[safeailab-eagle]].
