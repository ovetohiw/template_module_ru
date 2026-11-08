# docs (analyst)

**Who reads:** analyst only. **Who does not:** other modules.

## Must

- Full scenarios live under `orchestrator/cases/current/behavior/` — not pasted into FEATURE.
- FEATURE holds short contract + `Behavior paths:` (links only) + empty `Security must/should` stubs for security hop to fill.

- Observable behavior only: input, output, errors, refusals — no internal implementation as acceptance.
- Empty acceptance or empty behavior paths with non-empty criteria → Spec hop `pass` forbidden.
- Unknown observable behavior → hard to human; do not invent scenarios.
- Accept: sync behavior to accepted truth or record `unchanged` + reason before close.

## Should

- One scenario file per user-visible path; name files clearly.
- Keep process/DoD out of behavior files.

## Forbidden

- Writing product code in Spec/Accept.
- Putting roles, G-gates, soft/hard, or harness process into behavior corpus.
- Secrets / real PII in FEATURE or behavior.
- Copying foreign module conventions into case docs.
