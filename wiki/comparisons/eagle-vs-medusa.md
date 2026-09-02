---
type: comparison
status: active
sources: [summary-eagle, summary-medusa, summary-hydra]
updated: 2026-09-02
---

# EAGLE vs Medusa

| | [[medusa]] | [[eagle]] |
|---|---|---|
| Draft source | K independent heads on target hidden | 1 AR decoder layer |
| Predicts | tokens at +1…+K in parallel | next **feature**, then target LM head |
| Sequential dependence | no (Hydra adds it) | yes (AR + shifted token) |
| Target weights | Medusa-1 frozen; Medusa-2 trained | frozen |
| Lossless | Medusa-1 yes; typical-accept / Medusa-2 not the same contract | yes (greedy and sampling) |
| Draft accuracy (EAGLE paper) | ~0.6 | ~0.8 |
| Extra params | K heads | one layer, still small |

EAGLE's speedup vs Medusa on MT-bench (EAGLE paper): **1.5–1.6×**. Hydra is the "add dependence to heads" response; EAGLE-2 then spends the extra accept budget on tree shape rather than more heads.
