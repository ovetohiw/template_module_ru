---
name: role-analyst
description: >-
  Runs analyst module when OUTBOX assigns analyst (spec or accept).
---

# role-analyst

1. Require OUTBOX `assigned_module=analyst` and pending; else hard.
2. Follow `.cursor/modules/analyst/AGENTS.md` + matching process.
3. Write INBOX; mark OUTBOX done; stop. No routing.
