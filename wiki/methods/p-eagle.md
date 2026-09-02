---
type: method
status: active
sources: [summary-p-eagle]
updated: 2026-09-02
---

# P-EAGLE

AWS parallel drafter on the EAGLE-3 stack. Learnable shared hidden state predicts K draft tokens in **one** drafter forward. Training scales to ~20k ctx via mask precompute + sequence partition.

Speedup is **1.10–1.36× over EAGLE-3**, not over vanilla AR. Aimed at long reasoning traces in vLLM.
