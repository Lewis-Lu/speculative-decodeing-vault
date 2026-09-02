---
type: concept
status: active
sources: [summary-eagle-3]
updated: 2026-09-02
---

# Training-time test

EAGLE-3 training trick. Unroll the drafter at train time so later steps see **self-generated** features/tokens, matching inference. Enables dropping feature-prediction loss.

Without it, extra data raises first-token accept but second-token accept crashes (train/test input mismatch). With it, fused low/mid/high features become usable because the model is no longer required to output a valid top-layer feature.

Related: DeepSeek MTP; ViSpec also uses multi-token prediction (and warns about hidden-state shortcuts).
