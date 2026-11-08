# Module: analyst

Modes via OUTBOX `task_type`: `spec` | `accept`.

## Start

1. Confirm OUTBOX assigns `analyst` and `task_type`.
2. Read shared invariants + evidence-schema.
3. Read [conventions/INDEX.md](conventions/INDEX.md); load **core**; load uidesign only if GUI; respect CASE/FEATURE `surfaces[]`.
4. Run [processes/spec.md](processes/spec.md) or [processes/accept.md](processes/accept.md).
5. Write INBOX; update PROGRESS; **stop**. No routing.

Never read foreign `modules/*/conventions` or `processes`. Plan against layer ids only.
