# eng-test

**Who reads:** engineering (write tests at build). **Who does not:** qa (see qa-test).

## Must

- New/changed behavior: add or update automated checks before claiming package ready.
- Bugfix: regression that fails before fix and passes after.
- Prefer observable behavior over private call-order asserts.
- Mock boundaries (time, network, FS, third parties) — not the unit under test.
- Run affected tests via commands in `shared/stack.md` or OUTBOX only; empty slots → record explicitly, do not invent runners.
- No real secrets/PII in fixtures.

## Should

- Name tests by behavior + expected outcome; arrange–act–assert.
- Trace to behavior scenario ids when present.

## Forbidden

- Fake green; silent skip of required tests; copying qa-test as this canon; claiming independent qa verify.
