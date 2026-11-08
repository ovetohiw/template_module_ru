# Process: spec

## Do

1. Read [../conventions/INDEX.md](../conventions/INDEX.md) (docs.md; uidesign.md if UI).
2. Read raw brief from CASE / OUTBOX (not from other modules).
3. Fill `cases/current/FEATURE.md` — observable behavior, scope in/out, acceptance.
4. Write behavior scenarios under `cases/current/behavior/` (one file per scenario).
5. Produce `work_packages[]` for abstract layers only; write `cases/current/plan.md`.
6. List open_questions; hard-stop if behavior cannot be stated without guessing.

## Do not

- Write product code
- Name module folders in packages
- Route to security/qa/engineering
- Skip empty acceptance

## Out

INBOX verdict `pass` or `needs_input`/`blocked` with requirements payload.
