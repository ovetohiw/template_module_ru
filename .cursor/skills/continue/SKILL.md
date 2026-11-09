---
name: continue
description: >-
  Продолжает активный кейс из файлов. Для /continue или продолжения
  пайплайна без угадывания роли.
---

# continue

1. Читай только orchestrator CASE + PROGRESS + OUTBOX + INBOX.
2. Если OUTBOX pending → скажи пользователю запустить соответствующий `role-*` (или запусти этот skill); не маршрутизируй.
3. Если INBOX pending → ход маршрутизации оркестратора по `.cursor/orchestrator/AGENTS.md`.
4. Никогда не invent роль из чата. Никогда не стартуй две роли в одном ходе.
