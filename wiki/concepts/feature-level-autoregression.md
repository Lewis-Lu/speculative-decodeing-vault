---
type: concept
status: active
sources: [summary-eagle]
updated: 2026-09-02
---

# Feature-level autoregression

EAGLE-1/2: the drafter predicts the target's **pre-LM-head hidden state**, then the **target LM head** turns that into a token distribution.

Claim: feature sequences are more regular than token sequences, so a 1-layer drafter can match the target better than token-level AR (Vicuna-7B ablation: 1.9× vs 1.5× before the shifted-token trick).

EAGLE-3 **abandons** this (feature loss was a capacity cap) in favor of direct token prediction + multi-layer fusion. See [[training-time-test]].
