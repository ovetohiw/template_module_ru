# Using this template

Copy into a product repo: root `AGENTS.md` + entire `.cursor/` (+ this README stub pattern).

## After clone

1. **Delete** [SCAFFOLD](SCAFFOLD) in a real product (must).
2. Fill root [README.md](../README.md) for the product only.
3. Fill [shared/stack.md](shared/stack.md) when commands exist.
4. Optional MCP: keep [mcp.json](mcp.json) empty until needed; enable servers via snippet in [shared/mcp-tools.md](shared/mcp-tools.md) (pin versions; `${env:NAME}` only).
5. Start: `/new-case` + brief → OUTBOX analyst. Continue with `/continue` / role skills per OUTBOX (`role-design` when assigned).

## Day-to-day

- Map: [INDEX.md](INDEX.md)
- Orchestrator: [orchestrator/AGENTS.md](orchestrator/AGENTS.md)
- Principles: [shared/harness-principles.md](shared/harness-principles.md)
- Golden demo: [orchestrator/cases/current/](orchestrator/cases/current/)
- Visual fidelity: lay out [refs/](orchestrator/cases/current/refs/) + `_index.md` → design hop → pack under [design/](orchestrator/cases/current/design/) → eng/qa consume pack

## Conventions

- Live under `modules/<role>/conventions/` with **role prefixes** (`eng-*`, `qa-*`, `sec-*`, `analyst-*`, `design-*`).
- Modules read **only their own**; conventions **never** travel via OUTBOX.
- CASE/FEATURE field `surfaces: []` ⊂ {web, desktop, bots} gates `*-web|desktop|bots` files.
- Domain files (`eng-db|network|io`) open only when the package touches that domain.
- `eng-ui` loads only when CASE `design_status=done`.
- Runners: `shared/stack.md` (allowed shared read — not a convention relay).
- MCP policy: `shared/mcp-tools.md` (allowed shared read; gate ≠ enabled server).
- eng / sec / qa / design keep different angles — no copy-paste canon.

## Editing this template

Read [shared/harness-principles.md](shared/harness-principles.md) and [rules/harness-edit.mdc](rules/harness-edit.mdc).

- Soft: one-module process; prefixed convention edits in owning module + INDEX; MCP server without secrets + mcp-tools.md line.
- Hard: shared/overlays conventions; universal conventions; unprefixed collisions; cross-role copy; convention relay; surfaces outside web/desktop/bots without human; empty stubs; fat root AGENTS; peer-handoff; secrets in mcp.json; `@latest` MCP default; always-on eval/XSS MCP; add/remove modules / FSM without human hard.
- Log in [shared/harness-changelog.md](shared/harness-changelog.md).

## Manual audit

| Check | Result |
|-------|--------|
| raw intake → qa OUTBOX? | NO |
| process outside `.cursor/`? | NO |
| root AGENTS thin? | YES |
| conventions local + prefixed? | YES |
| `design-*` prefix + design module? | YES |
| design = stage hop, not work_package? | YES |
| analyst ≠ visual extraction? | YES |
| eng-ui only when design_status=done? | YES |
| design_skip policy documented? | YES |
| rework_target on qa fail? | YES |
| `surfaces[]` gate? | YES |
| eng-test ≠ qa-test? | YES |
| qa-desktop present? | YES |
| shared/stack OK for runners? | YES |
| mcp-tools shared read? | YES |
| secrets in mcp.json? | NO |
| default mcpServers empty? | YES |
| convention OUTBOX relay? | NO |
| golden design_skip + design_status=skipped? | YES |
