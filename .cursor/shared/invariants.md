# Runtime invariants (исполнение кейса)

## Soft (реши и продолжай)

- Выбор реализации внутри FEATURE + слотов stack
- Уточнение из назначенных путей артефактов в OUTBOX
- Узкий фикс, нужный чтобы закрыть DoD текущего пакета, без расширения scope кейса

## Hard (стоп; blocker в orchestrator PROGRESS)

- Угадывать роль / следующий модуль из чата вместо CASE+OUTBOX
- Читать чужие process модулей
- Писать `to_role` / peer handoff
- Продвигать lifecycle по неполному envelope
- Помечать done без строк evidence
- Self-close: та же сессия закрывает build verify и accept
- Invent verify runners, не перечисленных в `stack.md` (использование MCP-инструментов по `shared/mcp-tools.md` — не invented runner; invented = произвольный CLI вне stack/OUTBOX)
- Стартовать соседнюю роль после DoD модуля в том же ходе
- Параллельный OUTBOX (v1 только serial)
- Менять структуру харнесса во время исполнения кейса
- Invent `design_skip` из чата; запускать plan_review при `design_status=pending`; eng freestyle UI когда `design_status=done` (обязан следовать pack)

## Evidence

Done требует schema в `evidence-schema.md`. Пустое или однословное доказательство невалидно.
