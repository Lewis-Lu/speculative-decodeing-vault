---
type: comparison
status: active
sources: [summary-eagle, summary-eagle-2, summary-eagle-3, summary-p-eagle]
updated: 2026-09-02
---

# EAGLE lineage

| Stage | What changed | Still the same | Typical cited speedup | Training |
|---|---|---|---|---|
| [[vanilla-speculative-decoding]] | small sibling LM, chain | Leviathan verify | 2–3× (T5-XXL / Chinchilla 70B) | none on target |
| [[eagle]] | 1-layer **feature** AR + shifted token + **static tree** | frozen target, lossless | 2.7–3.5× LLaMA2-Chat 70B | ~ShareGPT, 1–2 days |
| [[eagle-2]] | [[dynamic-draft-tree]] from confidence | same weights as EAGLE | 3.05–4.26×; +20–40% vs EAGLE | **none extra** |
| [[eagle-3]] | token pred, multi-layer fusion, [[training-time-test]] | EAGLE-2 trees | up to 6.5×; ~1.4× vs EAGLE-2; SGLang BS64 +1.38× | more data (~8×) |
| [[p-eagle]] | **parallel** K-token draft, long-ctx train | EAGLE-3-style target features | **1.10–1.36× vs EAGLE-3** | long sequences to 20k |

VLM side branch: [[eaglevlm]] is an EAGLE-2 port; [[specvlm]] / [[vispec]] add vision-specific draft inputs. See [[llm-vs-vlm-speculative-decoding]].
