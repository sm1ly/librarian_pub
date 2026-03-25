---
name: git_commit
description: Version control protocol. Commits file system state to Git to maintain an Audit Trail.
---

## АЛГОРИТМ
1. Перейди в корень базы знаний: `cd /mnt/z/obsidian/`
2. Выполни: `git add -A`
3. Выполни: `git commit -m "[message]"`, подставив переданный тебе аргумент.
4. Если терминал возвращает "nothing to commit, working tree clean", игнорируй это и продолжай работу.

Пример:

    cd /mnt/z/obsidian/ && git add -A && git commit -m "Librarian [Upsert]: добавлена статья о VPN"