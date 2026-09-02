---
type: synthesis
status: active
tags: [thesis]
updated: 2026-09-02
sources: [summary-eagle, summary-eagle-2, summary-eagle-3, summary-specvlm, summary-vispec, summary-p-eagle]
---

# Synthesis

Working thesis, not settled fact. Update this when a new source moves the argument.

## Claim 1 — Draft *quality under tiny capacity* is the LLM game

Vanilla speculative decoding wins when a cheap, distribution-matched sibling LM exists. That assumption breaks at the small end of a model family and for instruct-tuned mismatches ([[summary-eagle]]). The EAGLE bet: steal the target's pre-head features, predict the next feature, then reuse the target LM head. Feature space is more regular than tokens, but sampling hides which branch the feature sequence took — hence the shifted-token input ([[feature-uncertainty]]).

That single idea (feature AR + shifted token + tree verify) is why EAGLE beat Medusa/Lookahead on lossless speedup without a second full LM.

## Claim 2 — After EAGLE, the remaining LLM gains are *allocation* then *trainability*

- EAGLE-2: static trees waste budget on low-probability siblings. Confidence ≈ acceptance, so grow a [[dynamic-draft-tree]]. No new training.
- EAGLE-3: feature prediction is a **capacity constraint**. Removing it, simulating multi-step draft during training ([[training-time-test]]), and fusing multi-layer features lets extra data actually raise speedup (the scaling curve EAGLE-1/2 did not show).
- P-EAGLE: sequential drafting becomes the new serial bottleneck once accepted length is high and generations are long (reasoning models). Parallel draft trades some acceptance for fewer drafter forwards.

Read as a stack, not a replacement list: 3 still uses 2's tree; P still sits on 3.

## Claim 3 — VLMs fail if you only spec-decode the language tail

Two extra problems:

1. **Prefill / KV** scale with visual tokens ([[visual-token-bottleneck]]). Speculative decoding does not shrink vision-encoder time; compressors do.
2. **Draft–target vision gap.** The target filters redundant patches over many layers; a 1-layer drafter attends itself into mush ([[summary-vispec]]). So the drafter needs a compressed visual view *plus* some global visual cue on every text token.

SpecVLM attacks (1) with an elastic compressor and cheap online distillation. ViSpec attacks (2) with adaptor + global feature, and attacks data (short VQA answers) by synthesizing long responses. EagleVLM shows that naive EAGLE-2 port is already ~2×, not 3–4×.

**Tension (unresolved):** SpecVLM and ViSpec both claim to be the first practical VLM specdec. Benchmarks, models, and whether compression is "in" the speedup differ. Do not merge their 2.5–2.9× and ~3× numbers. Track in [[specvlm-vs-vispec]].

## Claim 4 — Lossless is a product constraint, not a default

EAGLE / EAGLE-2 / EAGLE-3 / SpecVLM advertise distribution identity via standard [[draft-and-verify]]. Medusa-2 finetunes the backbone; Medusa's typical-acceptance and some non-greedy recipes are lossy. Always tag the recipe.

## Open questions

- Does EAGLE-3's training-time test + multi-layer fusion transfer cleanly to VLMs, or do visual tokens make fused features leak shortcuts? (ViSpec worries about hidden-state shortcuts.)
- Where does parallel drafting (P-EAGLE / Medusa-like heads) beat sequential EAGLE-3 on *batch* throughput, not batch-1 latency?
- Video / high-res: is compressor choice (SpecVLM) or adaptor (ViSpec) the dominant term once prefill dwarfs decode?
- Serving: SGLang's +1.38× throughput at BS=64 for EAGLE-3 vs the folklore that specdec hurts large-batch throughput.

Next sources worth ingesting: HASS, Falcon, Spec-Bench, LayerSkip, MagicDec, MMSPEC.
