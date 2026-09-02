# SpeculativeDecoding LLM Wiki — Schema

Vault-local copy. Canonical workspace copy: `../../AGENTS.md` (Cursor project root). Keep them in sync.

This folder is the **git repo and Obsidian vault**. Parent `../_ops/` holds Karpathy/llm-wiki notes so they do not appear in the knowledge graph. This file is listed in Obsidian `userIgnoreFilters`.

## Domain

Speculative decoding for faster LLM / VLM inference, with the **EAGLE family** as the hub.

## Three layers

| Layer | Path | Who writes | Mutability |
|---|---|---|---|
| Raw sources | `raw/` | Human (agent may *add* files, never edit existing ones) | Immutable after ingest |
| Wiki | `wiki/` | LLM only | Living; rewrite freely |
| Schema | this file + workspace `.cursor/rules/llm-wiki.mdc` | Human + LLM co-evolve | Slow-changing |

Never modify files under `raw/` except to *add* a new source. Never invent citations.

Do not add process/meta pages under `wiki/`. Put those in `../_ops/`.

## Directory map

```
Home.md
raw/papers/
raw/papers/txt/
raw/articles/
raw/assets/
wiki/index.md
wiki/log.md
wiki/overview.md
wiki/synthesis.md
wiki/sources/
wiki/concepts/
wiki/methods/
wiki/entities/
wiki/comparisons/
```

## Operations (short)

- **Ingest:** add raw file → write `wiki/sources/summary-*.md` → update linked pages → `index.md` → append `log.md`.
- **Query:** read `index.md` → open 3–8 pages → cite them → file reusable answers.
- **Lint:** contradictions, stale numbers, orphans, missing pages.

Full conventions (frontmatter, speedup citation rules, EAGLE lineage) are in the workspace-root `AGENTS.md`.
