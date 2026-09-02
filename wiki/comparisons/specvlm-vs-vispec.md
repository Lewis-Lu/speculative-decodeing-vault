---
type: comparison
status: active
sources: [summary-specvlm, summary-vispec]
updated: 2026-09-02
---

# SpecVLM vs ViSpec

Concurrent 2025 VLM specdec papers. **Not a head-to-head.** Different models, benches, and whether vision compression is in the loop.

| | [[specvlm]] | [[vispec]] |
|---|---|---|
| Venue | arXiv, AMD + XJTU | NeurIPS 2025, PKU + Huawei |
| Diagnosis | visual **token count** / draft prefill + no offline distill corpus | visual **redundancy** a shallow drafter cannot filter |
| EAGLE relation | EagleVLM = EAGLE-2 baseline | EAGLE-2 trees + EAGLE-like global feature on text |
| Extra machinery | elastic compressor (prune/pool/conv/resample); [[online-logit-distillation]] | vision adaptor; global visual vector; long-response synthesis; MTP vs shortcuts |
| Headline | EagleVLM 1.5–2.3×; SpecVLM **2.5–2.9×** E2E, 5 epochs, LLaVA/MMMU, lossless | "first substantial" VLM specdec; Fig. 1 beats Medusa & EAGLE-2 on LLaVA-1.6 and Qwen2.5-VL (GQA, T=0) |
| Code | haiduo/SpecVLM | KangJialiang/ViSpec |

**Open:** a shared table on LLaVA-1.6-7B / same bench / same GPU is missing. Until then, treat both as complementary attacks on the VLM draft, not ranked winners.
