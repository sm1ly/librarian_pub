---
name: librarian
description: Spawn librarian teammate into library team. Use when you need to ingest files into KB vault or retrieve deep knowledge.
argument-hint: [optional task message for librarian]
---

## Sequence

0. **Clean up Library team**
   ```
   TeamDelete(team_name="library")
   ```

1. **Create team:**
   ```
   TeamCreate(team_name="library", description="Knowledge base management team")
   ```

2. **Create persistent task (if argument provided):**
   ```
   TaskCreate(subject="Knowledge Base Operations", description=<task>)
   ```

3. **Spawn librarian:**
   ```
   Agent(
     description="Spawn librarian into library team",
     prompt="Инициализируйся. Ты библиотекарь в тиме library. Вызови TaskList(), забери задачу в работу и выполняй.",
     subagent_type="librarian",
     team_name="library",
     name="librarian",
     run_in_background=true
   )
   ```

## Notes
- Librarian runs as Sonnet with bypassPermissions.
- Sequential ingestion only — never spawn multiple librarians in parallel.
- Tasks are persisted via TaskCreate to survive context compaction.
- To shut down safely: `SendMessage(to="librarian", message={type: "shutdown_request"})`
