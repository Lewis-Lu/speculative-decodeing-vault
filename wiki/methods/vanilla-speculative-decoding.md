---
type: method
status: active
sources: [summary-leviathan-speculative-decoding, summary-chen-speculative-sampling]
updated: 2026-09-02
---

# Vanilla speculative decoding

Independent smaller **LM** drafts a **chain**; target verifies with Leviathan/Chen sampling. Needs a distribution-matched sibling (same tokenizer / chat template). EAGLE: 7B drafting 13B is often net-negative; 7B has no cheaper sibling → N/A on their plots.

[[speculative-decoding]] · [[draft-and-verify]]
