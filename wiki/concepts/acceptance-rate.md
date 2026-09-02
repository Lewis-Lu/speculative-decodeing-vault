---
type: concept
status: active
sources: [summary-eagle-2]
updated: 2026-09-02
---

# Acceptance rate

Probability a drafted token survives verification. Drives expected accepted length \(\sigma\), which (with draft latency \(T_q\)) dominates speedup.

EAGLE-2: rate is **context-dependent**, not only a function of tree position. EAGLE draft **confidence ≈ acceptance** (calibration), which licenses [[dynamic-draft-tree]].

EAGLE-3 plots 0-α vs 1-α (first vs second drafted token) to show why feature-loss removal without [[training-time-test]] fails.
