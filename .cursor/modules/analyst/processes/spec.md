# Process: spec

## Do

1. Read [../conventions/INDEX.md](../conventions/INDEX.md) → analyst-docs; analyst-uidesign if GUI.
2. Set CASE/FEATURE `surfaces: []` (web|desktop|bots) from the brief.
3. Read raw brief from CASE / OUTBOX (not other modules).
4. Fill FEATURE — goal, scope, acceptance, behavior paths, Security stubs.
5. Write behavior under `cases/current/behavior/`.
6. Produce `work_packages[]` (layer ids only) → `plan.md`.
7. Hard-stop if behavior unknown.

## Do not

- Product code; module folder names in packages; route to other roles; empty acceptance.

## Out

INBOX `pass` | `needs_input` | `blocked` with requirements payload.
