# Librarian

**Autonomous Knowledge Base Architect for Claude Code**

Librarian is a Claude Code agent (teammate) that manages an Obsidian Vault as a structured knowledge base with a three-tier memory architecture. It ingests raw data, filters garbage, performs semantic merges, and maintains ClickHouse indexes — all autonomously.

## Architecture: L0 / L1 / L2

```
L0  Embedding Index    TEI + ClickHouse    Cosine similarity, milliseconds
L1  Summary Index      ClickHouse          YAML frontmatter: title, summary, tags, domain
L2  Full Articles      Obsidian Vault      Markdown files with YAML frontmatter
```

- **L0** — vector embeddings for associative retrieval (semantic search)
- **L1** — structured metadata in ClickHouse (`kb.articles` table, Bloom filters on tags)
- **L2** — full markdown articles in an Obsidian vault, organized by domain

## How It Works

```
raw data → _inbox/ → Chunker (>50KB) → file_parse (Zero-Value filter + synthesis)
    → /kb search for duplicates → Merge / Create / Drop
    → /git_commit → /kbupd (sync L1 index)
```

1. **Inbox**: Drop raw files (memory dumps, logs, notes) into `_inbox/`
2. **Chunker** (Haiku subagent): Splits files >50KB into semantic chunks, quarantines toxic content
3. **file_parse**: Evaluates content value (Zero-Value Protocol — drops garbage), extracts engineering essence, generates YAML frontmatter
4. **Dedup**: Searches existing KB via `/kb` skill (ClickHouse Bloom filters)
5. **Merge Logic**: Semantic merge into existing article, or create new one. Lossless fact retention — never drop details for readability
6. **Persist**: Git commit + ClickHouse L1 index sync

## Agent Definitions

### Librarian (Sonnet)
The main agent. Owns the vault, runs the pipeline, makes merge/create/drop decisions.

```yaml
# .claude/agents/librarian.md
name: librarian
model: claude-sonnet-4-6
permissionMode: bypassPermissions
```

### Chunker (Haiku)
Subagent spawned by Librarian for large files. Splits semantically, quarantines junk, returns file listing, dies.

```yaml
# .claude/agents/chunker.md
name: chunker
model: claude-haiku-4-6
permissionMode: bypassPermissions
```

## Skills

| Skill | Description |
|-------|-------------|
| **file_parse** | Zero-Value filter + adaptive extraction. Drops garbage, synthesizes content into structured markdown with YAML frontmatter. Domain-aware: infra → architecture decisions; AI → mechanism analysis; science → causal chains. |
| **kbupd** | Parses YAML frontmatter from `.md` files and UPSERTs into ClickHouse `kb.articles` table. |
| **git_commit** | Commits vault state to git for audit trail. |
| **kb** | Queries ClickHouse for existing articles by domain, tags, or search. Returns L1 summaries and L2 vault paths. |
| **librarian** | Orchestrator skill — spawns the librarian agent into a team with persistent tasks. |

## YAML Schema (kb.articles)

Every article in the vault has YAML frontmatter:

```yaml
---
domain: "infra"
category: "clickhouse"
title: "L0/L1 Knowledge Base Schema"
title_ru: "Схема L0/L1 базы знаний"
summary: "DDL for kb.articles table using ReplacingMergeTree with Bloom filters."
tags_en: ["database", "schema", "architecture"]
tags_ru: ["база_данных", "схема", "архитектура"]
source: "user"
---
```

## Key Design Decisions

- **Sequential only** — never spawn multiple librarians in parallel (race condition on dedup)
- **Zero-Value Protocol** — ruthless garbage filter before any processing
- **Semantic merge, not concatenation** — new facts integrated into existing document structure
- **Lossless fact retention** — isolated notes section for facts that don't fit the main structure
- **Chunker quarantine** — toxic/jailbreak content isolated, never enters KB

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) with agent support
- Obsidian vault (or any markdown file structure)
- ClickHouse for L0/L1 indexes (optional — works without it as pure file-based KB)
- [TEI](https://huggingface.co/docs/text-embeddings-inference) for L0 embeddings (optional)

## Installation

1. Copy agent definitions to `.claude/agents/`
2. Copy skills to `.claude/skills/` (or your skills directory)
3. Adapt hardcoded paths in the following files (see table below)
4. Set up ClickHouse `kb.articles` table (see Schema section)
5. Create `_inbox/` directory in your vault
6. Drop files into `_inbox/` and spawn the librarian

### Paths to Adapt

These files contain paths specific to the reference setup. Update them to match your environment:

| File | What to change |
|------|---------------|
| `agents/librarian.md` | `_inbox/` path, `_quarantine/` path, canonical folders root |
| `agents/chunker.md` | `_quarantine/` path, temp storage path |
| `skills/git_commit/SKILL.md` | Vault root path (for `cd` and `git add`) |
| `skills/kbupd/SKILL.md` | Path to `sync_l1_index.py` script |
| `skills/kb/SKILL.md` | ClickHouse connection details, `kbcli` path |
| `skills/librarian/SKILL.md` | Team name (if you want a different one) |

## License

MIT
