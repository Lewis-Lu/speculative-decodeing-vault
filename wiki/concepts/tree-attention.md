---
type: concept
status: active
sources: [summary-specinfer, summary-eagle]
updated: 2026-09-02
---

# Tree attention

Verify many prefixes that share a prompt by packing them as a tree and using a custom attention mask (each node attends to its ancestors, not its siblings). One target forward scores the whole tree.

Used by [[specinfer]], [[medusa]], [[eagle]]. Without it, you only have chain drafts.
