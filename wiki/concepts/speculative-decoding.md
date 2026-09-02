---
type: concept
status: active
tags: [foundational]
sources: [summary-leviathan-speculative-decoding, summary-chen-speculative-sampling]
updated: 2026-09-02
---

# Speculative decoding

Algorithmic pattern: a cheap **draft** proposes several future tokens; the expensive **target** verifies them in **one** (tree-aware) forward; a rejection rule keeps the **same distribution** as running the target alone ([[lossless-acceleration]], [[draft-and-verify]]).

It exploits [[memory-bandwidth-bound-decoding]]: extra parallel FLOPs are cheaper than extra serial weight loads.

Named in [[summary-leviathan-speculative-decoding]]; DeepMind variant [[summary-chen-speculative-sampling]]. Trees: [[specinfer]]. Feature drafters: [[eagle]]. VLMs: [[specvlm]], [[vispec]].
