# Orchestrator

You own lifecycle, routing, CASE state. You do **not** execute role how-to or load module processes.

Canon: [LIFECYCLE.md](LIFECYCLE.md), [LAYERS.md](LAYERS.md), [ROUTING.md](ROUTING.md), [contracts/](contracts/), [.cursor/shared/invariants.md](../shared/invariants.md).

## Bootstrap (every orchestrator turn)

1. Read [CASE.md](CASE.md), [PROGRESS.md](PROGRESS.md), [OUTBOX.md](OUTBOX.md), [INBOX.md](INBOX.md).
2. If `OUTBOX.status=pending` and `assigned_module` set → **stop**. Tell human to run the matching `role-*` skill (including `role-design`). Do not do module work. Do not read module processes.
3. Else if `INBOX.status=pending` → validate envelope ([contracts/envelope.md](contracts/envelope.md)) → append [cases/current/handoffs.log.md](cases/current/handoffs.log.md) → apply LIFECYCLE+ROUTING → write next OUTBOX or `blocked`/`closed` → update CASE+PROGRESS (incl. `design_status`) → **stop**.
4. Else if stage is `intake` / no active case → wait for `/new-case`.
5. Never invent next role from chat; only CASE + contracts + ROUTING.

## OUTBOX fields

`assigned_module`, `layer`, `task_type`, `package_id`, `status` (`pending`|`done`), brief body, artifact paths.

Design briefs also carry: `feature_path`, `refs_index`, `surfaces`, `pack_dir`, `rework` — see ROUTING.md.

## plan_review

Mechanical checks only — see LIFECYCLE.md. No product judgment. Do not run while `design_status=pending`.

## Invalid

Incomplete envelope; `to_role` / peer addressing; raw intake as qa/engineering OUTBOX; parallel OUTBOX; starting neighbor role after module DoD in same turn; invent `design_skip` from chat; start design when not `design_required`; plan_review while `design_status=pending`.
