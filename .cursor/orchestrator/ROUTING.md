# Routing

## Bind layer → module

| Layer | Module path | Skill |
|-------|-------------|-------|
| requirements | `.cursor/modules/analyst` | role-analyst (`task_type=spec`) |
| design | `.cursor/modules/design` | role-design |
| security | `.cursor/modules/security` | role-security |
| implementation | `.cursor/modules/engineering` | role-engineering |
| verification | `.cursor/modules/qa` | role-qa |
| acceptance | `.cursor/modules/analyst` | role-analyst (`task_type=accept`) |

## Serial order (v1)

After plan_review pass, issue packages in order:

1. all ready `security`
2. all ready `implementation`
3. all ready `verification`
4. then stage `acceptance`

Ready = deps satisfied. One OUTBOX at a time.

`design` is **not** in this serial list (stage-gate before plan_review, or design-rework mid-execution).

## Classification (INBOX → next)

### Analyst spec pass (including rework after plan_review fail)

Recompute `design_required` from FEATURE.surfaces + design_skip:

1. If `design_required` AND `design_status != done` → stage=`design`; `design_status=pending`; OUTBOX design
2. Else if `design_required` AND `design_status == done` → plan_review
3. Else if web|desktop in surfaces AND design_skip → `design_status=skipped`; plan_review
4. Else → `design_status=not_applicable`; plan_review

### Design

| Signal | Next |
|--------|------|
| design `pass` | `design_status=done`. If `design_rework_from=verification`: clear flag; re-issue same implementation package; stage=`execution`. Else → plan_review |
| design `needs_input` / `blocked` | stop; no plan_review; no impl |

### Plan review / execution / accept

| Signal | Next |
|--------|------|
| plan_review fail | analyst spec (blockers); keep `design_status=done` unless blockers say pack invalid |
| plan_review pass | first ready execution package |
| security `pass` | next ready package |
| security `blocked` | blocked / human |
| implementation `pass` | next ready package |
| verification `pass` | acceptance (when all verification packages done) |
| verification `fail` | see rework_target below |
| acceptance `pass` | closed |
| acceptance `fail` | rework → implementation (or requirements) |
| any incomplete envelope | hard; do not advance |
| payload contains `to_role` / peer address | invalid; hard |

### Verification fail → rework_target

Read `findings[].rework_target` (default `implementation` if missing):

| rework_target | Next |
|---------------|------|
| `implementation` | OUTBOX engineering (as today) |
| `design` | set `design_rework_from=verification`; stage=`design`; `design_status=pending`; OUTBOX design (`rework: true`) |
| `requirements` | OUTBOX analyst spec |

`round++` per fail class; max 2 → blocked.

## Design OUTBOX brief fields

```text
assigned_module: design
layer: design
status: pending
feature_path: cases/current/FEATURE.md
refs_index: cases/current/refs/_index.md
surfaces: []
pack_dir: cases/current/design/
rework: false|true
```

## Conventions

Do **not** copy or relay `modules/*/conventions` via OUTBOX. Downstream modules read FEATURE / plan / evidence / design pack paths and their **own** role-prefixed conventions only (gated by `surfaces[]`). Security must live in FEATURE after security hop. Design pack lives under FEATURE.design after design hop. `shared/stack.md` is allowed for runners. `shared/mcp-tools.md` is allowed for MCP policy (not a convention relay).
