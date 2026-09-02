---
type: concept
status: active
sources: [summary-leviathan-speculative-decoding, summary-eagle]
updated: 2026-09-02
---

# Lossless acceleration

Output distribution identical to vanilla target decoding (up to numerics). Requires:

- frozen target (or a verify rule that still matches it), and
- Leviathan/Chen acceptance, not relaxed "typical" gates.

EAGLE / EAGLE-2 / EAGLE-3 / SpecVLM advertise this. Medusa-1 can. Medusa-2 finetunes the backbone. Lookahead is exact for its Jacobi scheme but EAGLE papers treat non-greedy Medusa/Lookahead as not comparable.

Always pair a speedup number with whether it is lossless.
