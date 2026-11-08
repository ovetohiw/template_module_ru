# Routing

## Bind layer → module

| Layer | Module path | Skill |
|-------|-------------|-------|
| requirements | `.cursor/modules/analyst` | role-analyst (`task_type=spec`) |
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

## Classification (INBOX → next)

| Signal | Next |
|--------|------|
| analyst spec `pass` | plan_review |
| plan_review fail | analyst spec (blockers) |
| plan_review pass | first ready execution package |
| security `pass` | next ready package |
| security `blocked` | blocked / human |
| implementation `pass` | next ready package |
| verification `pass` | acceptance (when all verification packages done) |
| verification `fail` | rework → implementation (or requirements if acceptance gap) |
| acceptance `pass` | closed |
| acceptance `fail` | rework → implementation (or requirements) |
| any incomplete envelope | hard; do not advance |
| payload contains `to_role` / peer address | invalid; hard |

## Conventions

Do **not** copy or relay `modules/*/conventions` via OUTBOX. Downstream modules read FEATURE / plan / evidence and their **own** conventions only. Security must live in FEATURE after security hop.
