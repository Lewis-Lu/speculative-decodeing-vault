---
type: concept
status: active
sources: [summary-chen-speculative-sampling, summary-leviathan-speculative-decoding]
updated: 2026-09-02
---

# Draft and verify

Two-phase loop given prefix \(T_{1:j}\):

1. **Draft.** Produce \(\hat{T}_{j+1:j+k}\) and draft probs \(\hat{p}\). Implementation: small LM, heads, n-grams, or EAGLE-style layer.
2. **Verify.** One target forward yields \(p\) on the same positions (or a tree of them). Walk left-to-right: accept \(\hat{t}\) w.p. \(\min(1, p(\hat{t})/\hat{p}(\hat{t}))\); else sample \(\mathrm{norm}(\max(0,p-\hat{p}))\) and discard the suffix.

Chain drafts die at first reject. [[tree-attention]] keeps sibling branches. [[dynamic-draft-tree]] changes which branches you bother to verify.

This is the contract behind EAGLE 1–3 and SpecVLM's lossless claim. Medusa-2 / typical-acceptance may leave this contract.
