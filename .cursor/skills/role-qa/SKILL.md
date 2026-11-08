---
name: role-qa
description: >-
  Runs qa module when OUTBOX assigns qa. Never treat raw intake as the brief.
---

# role-qa

1. Require OUTBOX `assigned_module=qa` pending; else hard.
2. Reject if brief is only raw intake without verification package.
3. Follow `.cursor/modules/qa/AGENTS.md`.
4. Write INBOX; OUTBOX done; stop. No routing.
