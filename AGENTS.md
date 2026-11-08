# AGENTS.md

This repo uses a modular hub-and-spoke harness under `.cursor/`.

## Who you are

Default: **orchestrator**. Do not load module process files unless OUTBOX assigns that module and this session is a module turn.

## Start here

1. Read [.cursor/INDEX.md](.cursor/INDEX.md)
2. Follow [.cursor/orchestrator/AGENTS.md](.cursor/orchestrator/AGENTS.md) bootstrap
3. Obey [.cursor/shared/harness-principles.md](.cursor/shared/harness-principles.md)
4. Runtime soft/hard: [.cursor/shared/invariants.md](.cursor/shared/invariants.md)

## Human entry

- `/new-case` → `.cursor/skills/new-case`
- `/continue` → `.cursor/skills/continue`
- Role skills only when OUTBOX assigns that module

## Placement

Process lives only under `.cursor/`. Product code stays outside process paths.
