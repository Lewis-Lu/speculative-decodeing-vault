---
type: method
status: active
sources: [summary-eagle]
updated: 2026-09-02
---

# EAGLE

Extrapolation Algorithm for Greater Language-model Efficiency (Li et al., ICML 2024). One decoder layer: [[feature-level-autoregression]] + shifted token ([[feature-uncertainty]]) + tree draft ([[tree-attention]]). Frozen target. Train on ShareGPT-scale data, not a full small LM pretrain.

Headline: LLaMA2-Chat 70B **2.7–3.5×** latency, lossless. Draft acc ~0.8.

Family: [[eagle-framework]] → [[eagle-2]] → [[eagle-3]] → [[p-eagle]]. Code: [[safeailab-eagle]].
