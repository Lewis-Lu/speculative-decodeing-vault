---
type: concept
status: active
sources: [summary-eagle-2]
updated: 2026-09-02
---

# Dynamic draft tree

Static trees (EAGLE-1, Medusa): at step *i* always expand *k* children — implicit "accept rate depends only on position."

Dynamic (EAGLE-2): use draft confidence as a proxy for [[acceptance-rate]]; expand the valuable frontier; prune before verify. Same draft **weights**. Context-aware shape (easy token → deep/narrow; hard token → wide).

Reused by EAGLE-3, SpecVLM, ViSpec.
