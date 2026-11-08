# Using this template

Copy into a product repo: root `AGENTS.md` + entire `.cursor/` (+ this README stub pattern).

## After clone

1. **Delete** [.cursor/SCAFFOLD](SCAFFOLD) in a real product (must). While present, closed cases reset process-state.
2. Fill root [README.md](../README.md) for the product only.
3. Fill [.cursor/shared/stack.md](shared/stack.md) when commands exist.
4. Start work: `/new-case` + brief → OUTBOX analyst. Continue with `/continue` / role skills per OUTBOX.

## Day-to-day

- Map: [INDEX.md](INDEX.md)
- Orchestrator: [orchestrator/AGENTS.md](orchestrator/AGENTS.md)
- Principles: [shared/harness-principles.md](shared/harness-principles.md)
- Golden demo case: [orchestrator/cases/current/](orchestrator/cases/current/) (replace for real work)

## Conventions

Each module has role-specific rules under `modules/<role>/conventions/`. Modules read **only their own**. Conventions never travel via OUTBOX; case work uses FEATURE/plan/evidence/findings.

## Editing this template

Harness edit ≠ case execution. Read [shared/harness-principles.md](shared/harness-principles.md) and [rules/harness-edit.mdc](rules/harness-edit.mdc).

- Soft: one-module process clarify; role-specific convention edits inside one module; link fixes; INDEX sync.
- Hard: new/remove module; FSM/layers change; process outside `.cursor/`; fat root AGENTS; peer-handoff; weaken evidence; shared/overlays conventions; universal conventions; convention relay via contract; cross-read foreign conventions; empty convention stubs in shipped template.
- Log structural changes in [shared/harness-changelog.md](shared/harness-changelog.md) only.

## Manual audit (v1 ship) — 2026-11-08

| Check | Result |
|-------|--------|
| raw intake → qa OUTBOX? | NO (handoffs + qa skill) |
| process outside `.cursor/`? | NO |
| root AGENTS thin? | YES |
| parallel OUTBOX? | NO (serial v1) |
| handoffs.log append-only used? | YES |
| plan_review mechanical only? | YES |
| harness-edit alwaysApply? | NO |
| case PROGRESS ≠ harness-changelog? | YES |
| hub-and-spoke silently breakable without rule? | NO (invalid envelope + principles) |
| golden E2E + rework hop present? | YES |
| conventions local only (no OUTBOX relay)? | YES |
| convention files role-filled (not empty stubs)? | YES |
