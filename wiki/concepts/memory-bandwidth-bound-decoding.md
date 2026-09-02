---
type: concept
status: active
sources: [summary-leviathan-speculative-decoding, summary-lookahead]
updated: 2026-09-02
---

# Memory-bandwidth-bound decoding

Each AR step streams the full target weights from HBM. Arithmetic intensity is low, so GPUs sit on memory, not FLOPs. Speculative decoding, Medusa heads, and Lookahead all buy **fewer serial weight loads** by doing more parallel work per load.

Implication: draft overhead must stay small vs one target forward, and batching changes the math (EAGLE-3's SGLang BS=64 result is why we do not assume specdec only helps batch 1).
