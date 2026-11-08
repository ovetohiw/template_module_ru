---
name: role-engineering
description: >-
  Runs engineering module when OUTBOX assigns engineering.
---

# role-engineering

1. Require OUTBOX `assigned_module=engineering` pending; else hard.
2. Follow `.cursor/modules/engineering/AGENTS.md`.
3. Write INBOX; OUTBOX done; stop. No routing.
