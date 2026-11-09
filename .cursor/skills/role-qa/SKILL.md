---
name: role-qa
description: >-
  Запускает модуль qa, когда OUTBOX назначает qa. Никогда не считай сырой intake брифом.
---

# role-qa

1. Требуй OUTBOX `assigned_module=qa` pending; иначе hard.
2. Откажи, если brief — только сырой intake без verification package.
3. Следуй `.cursor/modules/qa/AGENTS.md`.
4. Запиши INBOX; OUTBOX done; стоп. Без routing.
