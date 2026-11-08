# analyst-docs

**Who reads:** analyst. **Who does not:** other modules.

## Must

- Scenarios under `cases/current/behavior/`; FEATURE keeps short contract + Behavior paths.
- Include `surfaces: []` (web|desktop|bots) on FEATURE; keep in sync with CASE.
- Leave Security must/should stubs for security hop to fill.
- Observable acceptance only; hard to human if behavior unknown.
- Accept: sync behavior or `unchanged` + reason.

## Should

- One scenario file per user-visible path.

## Forbidden

- Product code; secrets/PII in docs; process/DoD inside behavior files; foreign conventions.
