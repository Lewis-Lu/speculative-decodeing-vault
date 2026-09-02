---
type: concept
status: active
sources: [summary-specvlm]
updated: 2026-09-02
---

# Online logit distillation

SpecVLM draft training: teacher logits and penultimate features computed **on the fly** (CE + Smooth L1). Avoids storing a huge offline distillation corpus.

Paper reports a **training-time scaling** effect: more online steps → higher average accepted length, monotonically in their plots (within 5 epochs).
