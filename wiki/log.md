# Log

Append-only. `grep "^## \[" wiki/log.md | tail`.

## [2026-09-02] ingest | Initial corpus + LLM Wiki bootstrap

- Applied Karpathy LLM Wiki schema (`AGENTS.md`, `.cursor/rules/llm-wiki.mdc`).
- Downloaded 12 arXiv PDFs into `raw/papers/` and extracted `raw/papers/txt/`.
- Ingested: [[summary-leviathan-speculative-decoding]], [[summary-chen-speculative-sampling]], [[summary-specinfer]], [[summary-eagle]], [[summary-eagle-2]], [[summary-eagle-3]], [[summary-medusa]], [[summary-lookahead]], [[summary-hydra]], [[summary-specvlm]], [[summary-vispec]], [[summary-p-eagle]].
- Hub pages: [[overview]], [[synthesis]], [[eagle-lineage]], [[llm-vs-vlm-speculative-decoding]].

## [2026-09-02] lint | Move vault into git repo; drop meta from graph

- Knowledge files now live in `SpeculativeDecoding/speculative-decodeing-vault/` (`origin`: Lewis-Lu/speculative-decodeing-vault).
- Moved `llm-wiki` concept, Karpathy gist, and its summary to `SpeculativeDecoding/_ops/` so they are not Obsidian graph nodes.
