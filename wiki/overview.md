---
type: overview
status: active
tags: [map]
updated: 2026-09-02
---

# Overview

Autoregressive decode is [[memory-bandwidth-bound-decoding]]: each new token reloads the full target weights. [[speculative-decoding]] (Leviathan et al., Chen et al.) splits generation into a cheap **draft** and a parallel **verify**, with [[lossless-acceleration]] via rejection sampling.

The bottleneck then becomes: *who drafts, how, and at what acceptance?*

## LLM line (this vault's backbone)

1. **Vanilla** — smaller independent LM as drafter; chain of tokens. Works when a well-matched small sibling exists; fails for the smallest target in a family. [[vanilla-speculative-decoding]], [[summary-leviathan-speculative-decoding]], [[summary-chen-speculative-sampling]].
2. **Tree verify** — many candidate prefixes in one target forward. [[specinfer]], [[tree-attention]].
3. **Heads on the target** — Medusa / Hydra / Lookahead avoid a separate LM. High draft speed, lower draft quality. [[medusa]], [[hydra]], [[lookahead-decoding]].
4. **EAGLE** — one lightweight decoder layer that autoregresses at the **feature** (pre-LM-head) level, conditioned on a one-step-shifted token to kill [[feature-uncertainty]]. ~0.8 draft accuracy vs Medusa ~0.6. [[eagle]], [[feature-level-autoregression]].
5. **EAGLE-2** — same weights; [[dynamic-draft-tree]] grown from calibrated draft confidence. +20–40% over EAGLE. [[eagle-2]].
6. **EAGLE-3** — drop feature-prediction loss; [[training-time-test]]; fuse low/mid/high features; draft now **token-predicts**. Data scaling starts to work. Up to ~6.5× reported. [[eagle-3]].
7. **P-EAGLE** — draft *K* tokens in **one** drafter forward (learnable shared hidden state) so reasoning traces are not killed by sequential draft overhead. [[p-eagle]].

Code hub: [[safeailab-eagle]] ([SafeAILab/EAGLE](https://github.com/SafeAILab/EAGLE)). Serving: vLLM, SGLang, TensorRT-LLM.

## VLM line

Porting the above is not free. Visual tokens dominate **prefill** and KV cache; a tiny drafter cannot filter image redundancy the way the target can. [[visual-token-bottleneck]].

- [[eaglevlm]] — SpecVLM's EAGLE-2-style baseline: 1.5–2.3× end-to-end on LLaVA.
- [[specvlm]] — elastic visual compressor + [[online-logit-distillation]] → 2.5–2.9× on LLaVA/MMMU (5 epochs).
- [[vispec]] — vision adaptor + global visual feature on text tokens (EAGLE-style injection); claims first *substantial* VLM specdec speedup vs Medusa/EAGLE-2. [[vision-aware-drafting]].

See [[llm-vs-vlm-speculative-decoding]] and [[specvlm-vs-vispec]]. Numbers are **not** interchangeable across papers.

## How to read this wiki

Filed comparisons: [[eagle-lineage]], [[eagle-vs-medusa]]. Working argument: [[synthesis]]. Catalog: [[index]].
