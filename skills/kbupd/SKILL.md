---
name: kbupd
description: Parses YAML frontmatter from updated .md files and executes an UPSERT into the ClickHouse kb.articles table.
---

## АЛГОРИТМ
1. Вызывается Библиотекарем после `git_commit`.
2. Запусти Python-скрипт синхронизации индекса. Скрипт должен прочитать YAML frontmatter измененных файлов и залить их в БД.
3. Команда вызова:
   `python3 /home/sm1ly/llm_instances/memtools/sync_l1_index.py --file <vault_path>` (для одного файла)
   `python3 /home/sm1ly/llm_instances/memtools/sync_l1_index.py --all` (для полного ребилда)
4. Убедись, что вывод содержит `OK <vault_path>`. `SKIP` = нет YAML или обязательных полей. `FAIL` = ошибка записи.
