---
name: role-engineering
description: >-
  Запускает модуль engineering, когда OUTBOX назначает engineering.
---

# role-engineering

1. Требуй OUTBOX `assigned_module=engineering` pending; иначе hard.
2. Следуй `.cursor/modules/engineering/AGENTS.md`.
3. Запиши INBOX; OUTBOX done; стоп. Без routing.
