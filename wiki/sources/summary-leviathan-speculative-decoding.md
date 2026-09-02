---
type: source
status: ingested
title: Fast Inference from Transformers via Speculative Decoding
arxiv: 2211.17192
year: 2023
authors: [Yaniv Leviathan, Matan Kalman, Yossi Matias]
venue: ICML 2023 Oral
pdf: raw/papers/2211.17192_leviathan_speculative_decoding.pdf
txt: raw/papers/txt/2211.17192_leviathan_speculative_decoding.txt
tags: [llm, foundational]
related: [speculative-decoding, draft-and-verify, lossless-acceleration, vanilla-speculative-decoding]
updated: 2026-09-02
---

# Summary — Leviathan et al. (speculative decoding)

Google Research. The paper that **named** the algorithm.

## Problem

Decoding *K* tokens from a large Transformer is *K* serial forwards. Memory-bandwidth bound; extra FLOPs are cheap if they buy concurrency.

## Method

1. A cheaper approximation model proposes a prefix of tokens (speculative execution generalized to *maybe-needed* work).
2. The large model scores those tokens **in parallel** (one forward with a causal prefix).
3. [[draft-and-verify]] / speculative sampling accepts a prefix so the output distribution matches the large model exactly ([[lossless-acceleration]]).

No retraining of the target. Off-the-shelf pairs.

## Results to keep

- T5-XXL vs standard T5X: **2–3×** with identical outputs.
- Observation: hard LM tasks contain easy subtasks a small model can draft.

## What it changes here

This is the root node of [[speculative-decoding]] and [[vanilla-speculative-decoding]]. Concurrent with DeepMind [[summary-chen-speculative-sampling]]. EAGLE cites this for the acceptance proof.
