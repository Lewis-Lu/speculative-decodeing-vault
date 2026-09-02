---
type: concept
status: active
sources: [summary-vispec]
updated: 2026-09-02
---

# Vision-aware drafting

ViSpec's claim: a 1-layer drafter cannot filter redundant patches (attention mass drowned by repeated identical keys). Two injections:

1. Compressed visual tokens into draft attention, **original positions kept**.
2. One **global** visual vector added to subsequent text tokens (until next image) — analogue of EAGLE's target-feature injection.

Plus long-response synthetic data so the drafter sees more than 3-word VQA answers.
