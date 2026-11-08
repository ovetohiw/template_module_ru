---
name: continue
description: >-
  Continues the active case from files. Use for /continue or continue the
  pipeline without guessing the role.
---

# continue

1. Read orchestrator CASE + PROGRESS + OUTBOX + INBOX only.
2. If OUTBOX pending → tell user to run the matching `role-*` (or run that skill); do not route.
3. If INBOX pending → orchestrator routing turn per `.cursor/orchestrator/AGENTS.md`.
4. Never invent role from chat. Never start two roles in one turn.
