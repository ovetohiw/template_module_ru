---
name: role-analyst
description: >-
  Запускает модуль analyst, когда OUTBOX назначает analyst (spec или accept).
---

# role-analyst

1. Требуй OUTBOX `assigned_module=analyst` и pending; иначе hard.
2. Следуй `.cursor/modules/analyst/AGENTS.md` + соответствующий process.
3. Запиши INBOX; пометь OUTBOX done; стоп. Без routing.
