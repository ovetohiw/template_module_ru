---
name: role-security
description: >-
  Запускает модуль security, когда OUTBOX назначает security.
---

# role-security

1. Требуй OUTBOX `assigned_module=security` pending; иначе hard.
2. Следуй `.cursor/modules/security/AGENTS.md`.
3. Запиши INBOX; OUTBOX done; стоп. Без routing.
