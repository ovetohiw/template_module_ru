# Process: spec

## Do

1. Read [../conventions/INDEX.md](../conventions/INDEX.md) → analyst-docs; analyst-uidesign if GUI.
2. Set CASE/FEATURE `surfaces: []` (web|desktop|bots) from the brief.
3. Read raw brief from CASE / OUTBOX (not other modules).
4. Fill FEATURE — goal, scope, acceptance, behavior paths, Security stubs.
5. GUI (web|desktop): set FEATURE.design stubs (`refs_index`, `pack`); apply **design_skip policy**:
   - Forbidden skip if brief demands mockup/refs match OR refs/_index or refs/<screen>/ present → if refs missing, `needs_input`.
   - Allowed skip only with non-empty `design_skip_reason` (CRUD shell / no visual fidelity).
6. When `design_status` will be `done` (not skip): every `implementation` work_package must list design pack path in `artifacts_expected` or `constraints`.
7. Write behavior under `cases/current/behavior/`.
8. Produce `work_packages[]` — layers **only** `security` | `implementation` | `verification` → `plan.md`.
9. Hard-stop if behavior unknown.

## Do not

- Product code; module folder names in packages; `layer: design` in work_packages; visual pack synthesis; route to other roles; empty acceptance.

## Out

INBOX `pass` | `needs_input` | `blocked` with requirements payload.
