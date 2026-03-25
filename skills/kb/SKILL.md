---
name: kb
description: Queries the ClickHouse kb.articles table using exact matches and Bloom filters to retrieve L1 summaries and L2 vault paths.
argument-hint: [search terms]
---

## USAGE
Search the knowledge base via `kbcli`. Combine flags as needed.

**By text (title, title_ru, summary):**
```bash
kbcli --search "clickhouse migration"
```

**By tags:**
```bash
kbcli --tags infra,clickhouse
kbcli --tags-ru инфра,кликхаус
```

**By domain / category:**
```bash
kbcli --domain gaming --category slsns
```

**Combined:**
```bash
kbcli --domain ai --tags embeddings --last 5
```

**Output modes:**
```bash
kbcli --search "query" --pretty       # full details
kbcli --search "query" --json         # JSON lines for piping
kbcli --search "query" --paths-only   # vault_path only
```

## AFTER SEARCH
Analyze the returned `summary` (L1). If context is sufficient — use it. If you need full content — read the `vault_path` (L2) directly.
