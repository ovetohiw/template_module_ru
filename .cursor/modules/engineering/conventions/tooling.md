# tooling (engineering)

**Who reads:** engineering only. **Who does not:** qa (qa has its own test.md).

## Must

- Install/build/test commands only from `.cursor/shared/stack.md` or explicit OUTBOX hints.
- If stack slots empty: record that in module PROGRESS; do not invent CI commands.
- Fix red baseline checks before stacking new package work when those checks exist.

## Should

- Prefer repo scripts already wired in stack.md.
- Keep debug steps out of case evidence unless asked.

## Forbidden

- Fake “green” without running a listed command.
- Using qa’s process as a substitute for build tooling rules.
