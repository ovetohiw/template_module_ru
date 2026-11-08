# Runtime invariants (case execution)

## Soft (decide and continue)

- Implementation choice inside FEATURE + stack slots
- Clarify from assigned artifact paths in OUTBOX
- Narrow fix required to close current package DoD without expanding case scope

## Hard (stop; blocker in orchestrator PROGRESS)

- Guess role / next module from chat instead of CASE+OUTBOX
- Read foreign module processes
- Write `to_role` / peer handoff
- Advance lifecycle on incomplete envelope
- Mark done without evidence rows
- Self-close: same session finishes build verify and accept
- Invent verify runners not listed in `stack.md` (MCP tool use per `shared/mcp-tools.md` is not an invented runner; invented = arbitrary CLI outside stack/OUTBOX)
- Start neighbor role after module DoD in the same turn
- Parallel OUTBOX (v1 is serial only)
- Change harness structure during case execution
- Invent `design_skip` from chat; run plan_review while `design_status=pending`; eng freestyle UI when `design_status=done` (must follow pack)

## Evidence

Done requires schema in `evidence-schema.md`. Empty or one-word proof is invalid.
