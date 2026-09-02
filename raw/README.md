---
type: meta
status: active
updated: 2026-09-02
---

# Raw sources

Immutable corpus. The LLM reads these and compiles `wiki/`. Do not edit files here after they have been ingested.

| Folder | Contents |
|---|---|
| `papers/` | Canonical PDFs |
| `papers/txt/` | `pdftotext -layout` extracts — prefer these for ingest |
| `articles/` | Non-paper sources (Karpathy gist, notes) |
| `assets/` | Images / figures (Obsidian attachment folder) |

To add a paper: drop the PDF here, extract text, then ask the agent to **ingest** it.

## Papers in this corpus

| arXiv | File | Wiki summary |
|---|---|---|
| 2211.17192 | `2211.17192_leviathan_speculative_decoding.pdf` | [[summary-leviathan-speculative-decoding]] |
| 2302.01318 | `2302.01318_chen_speculative_sampling.pdf` | [[summary-chen-speculative-sampling]] |
| 2305.09781 | `2305.09781_specinfer.pdf` | [[summary-specinfer]] |
| 2401.15077 | `2401.15077_eagle.pdf` | [[summary-eagle]] |
| 2406.16858 | `2406.16858_eagle2.pdf` | [[summary-eagle-2]] |
| 2503.01840 | `2503.01840_eagle3.pdf` | [[summary-eagle-3]] |
| 2401.10774 | `2401.10774_medusa.pdf` | [[summary-medusa]] |
| 2402.02057 | `2402.02057_lookahead.pdf` | [[summary-lookahead]] |
| 2402.05109 | `2402.05109_hydra.pdf` | [[summary-hydra]] |
| 2509.11815 | `2509.11815_specvlm.pdf` | [[summary-specvlm]] |
| 2509.15235 | `2509.15235_vispec.pdf` | [[summary-vispec]] |
| 2602.01469 | `2602.01469_p_eagle.pdf` | [[summary-p-eagle]] |
