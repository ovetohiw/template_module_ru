# qa-test

**Who reads:** qa (independent verify). **Who does not:** engineering (eng-test).

## Must

- Verify FEATURE acceptance + behavior independently; evidence rows per `shared/evidence-schema.md` (`role=qa`).
- Runners only from `shared/stack.md` or OUTBOX; empty slots → explicit note, no invented runner.
- Optional MCP evidence tools only per `shared/mcp-tools.md` (not a runner-slot; not a `stack.md` replacement). No MCP ≠ skip verify — fall back to stack/manual; do not invent success. Note source in `command_or_action` (`mcp:…` / `stack:…` / `manual`).
- Prefer behavioral/e2e checks for critical paths; do not accept unit-on-mocks as sole proof of user path.
- Failures → findings[] (id, severity); verdict `fail` — do not assign eng yourself.
- Code-read alone ≠ pass when OUTBOX requires a run.
- No secrets/PII in evidence artifacts.

## Should

- Trace to behavior files; one clear failure reason per finding.
- Where multi-user resources exist, attempt cross-user access (IDOR pattern).

## Forbidden

- Raw intake as brief; summary-only pass; weakening asserts; foreign conventions; closing accept/case from qa.
