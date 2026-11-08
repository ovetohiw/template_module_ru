---
name: new-case
description: >-
  Opens a new orchestrator case from the user brief. Use for /new-case,
  новая задача, хочу фичу, or a natural-language product request when no
  active case is in progress.
---

# new-case

1. If CASE already active (stage not idle/closed) → hard; close or continue first.
2. Set CASE: new `case_id`, stage `analysis`, `surfaces: []` (analyst will fill), store `raw_brief`, status in progress.
3. Write OUTBOX: `assigned_module=analyst`, `layer=requirements`, `task_type=spec`, status pending.
4. Update orchestrator PROGRESS next_step → run role-analyst.
5. **Stop.** Do not run analyst in this turn.
