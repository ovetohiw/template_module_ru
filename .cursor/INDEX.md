# Harness map

| Path | Role |
|------|------|
| [../AGENTS.md](../AGENTS.md) | Thin root router |
| [orchestrator/AGENTS.md](orchestrator/AGENTS.md) | Lifecycle bootstrap |
| [orchestrator/LIFECYCLE.md](orchestrator/LIFECYCLE.md) | FSM + plan_review (+ design stage) |
| [orchestrator/LAYERS.md](orchestrator/LAYERS.md) | Abstract layers |
| [orchestrator/ROUTING.md](orchestrator/ROUTING.md) | Bind + serial order + design hops |
| [orchestrator/CASE.md](orchestrator/CASE.md) | Active case SoR (`design_status`) |
| [modules/](modules/) | Role harnesses (+ prefixed `conventions/`) |
| [modules/design/](modules/design/) | Design module (refs → visual pack) |
| [shared/harness-principles.md](shared/harness-principles.md) | Constitution |
| [shared/invariants.md](shared/invariants.md) | Runtime soft/hard |
| [shared/stack.md](shared/stack.md) | Verify/run command slots |
| [shared/mcp-tools.md](shared/mcp-tools.md) | MCP policy map (when / which) |
| [mcp.json](mcp.json) | Project MCP declarations (no secrets) |
| [TEMPLATE.md](TEMPLATE.md) | Human bootstrap + conventions map |
| [skills/](skills/) | Entry skills (`role-design`, …) |

CASE/FEATURE `surfaces: [web\|desktop\|bots]` gates surface convention files.

Visual refs: `orchestrator/cases/current/refs/` → design pack `cases/current/design/`.

Process stays under `.cursor/`. Product code does not mix with harness files.
