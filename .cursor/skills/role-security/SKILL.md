---
name: role-security
description: >-
  Runs security module when OUTBOX assigns security.
---

# role-security

1. Require OUTBOX `assigned_module=security` pending; else hard.
2. Follow `.cursor/modules/security/AGENTS.md`.
3. Write INBOX; OUTBOX done; stop. No routing.
