# test (qa)

**Who reads:** qa only. **Who does not:** engineering (eng has tooling.md).

## Must

- Independent verify against FEATURE acceptance + behavior paths.
- Evidence rows per `.cursor/shared/evidence-schema.md` (command, result, artifact, role=qa).
- Runners only from stack.md or OUTBOX; empty slots → explicit “slots empty” in evidence, no invented runner.
- Failures → findings[] with id/severity; verdict `fail` — do not route to eng yourself.
- Code-read alone ≠ pass when OUTBOX requires a behavioral check.

## Should

- Trace checks to scenario files under `cases/current/behavior/` when present.
- Prefer one clear failure reason per finding.

## Forbidden

- Treating raw user intake as the verification brief.
- Summary-only pass (“ok”, “зелёное”).
- Weakening asserts to force green.
- Reading or importing other modules’ conventions via OUTBOX.
- Closing the whole case / accept hop from qa.
