# Карта харнесса

| Путь | Роль |
|------|------|
| [../AGENTS.md](../AGENTS.md) | Тонкий корневой роутер |
| [orchestrator/AGENTS.md](orchestrator/AGENTS.md) | Bootstrap жизненного цикла |
| [orchestrator/LIFECYCLE.md](orchestrator/LIFECYCLE.md) | FSM + plan_review (+ стадия design) |
| [orchestrator/LAYERS.md](orchestrator/LAYERS.md) | Абстрактные слои |
| [orchestrator/ROUTING.md](orchestrator/ROUTING.md) | Bind + serial order + design hops |
| [orchestrator/CASE.md](orchestrator/CASE.md) | SoR активного кейса (`design_status`) |
| [modules/](modules/) | Ролевые харнессы (+ prefixed `conventions/`) |
| [modules/design/](modules/design/) | Модуль design (refs → visual pack) |
| [shared/harness-principles.md](shared/harness-principles.md) | Конституция |
| [shared/invariants.md](shared/invariants.md) | Runtime soft/hard |
| [shared/stack.md](shared/stack.md) | Слоты verify/run команд |
| [shared/mcp-tools.md](shared/mcp-tools.md) | Карта политики MCP (когда / какие) |
| [mcp.json](mcp.json) | Декларации MCP проекта (без секретов) |
| [TEMPLATE.md](TEMPLATE.md) | Человеческий bootstrap + карта conventions |
| [skills/](skills/) | Entry skills (`role-design`, …) |

CASE/FEATURE `surfaces: [web\|desktop\|bots]` гейтит surface convention файлы.

Visual refs: `orchestrator/cases/current/refs/` → design pack `cases/current/design/`.

Процесс остаётся под `.cursor/`. Код продукта не смешивается с файлами харнесса.
