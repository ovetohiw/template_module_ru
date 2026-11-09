# Как пользоваться этим шаблоном

Скопируй в продуктовый репозиторий: корневой `AGENTS.md` + весь `.cursor/` (+ паттерн README stub).

## После клона

1. **Удали** [SCAFFOLD](SCAFFOLD) в реальном продукте (обязательно).
2. Заполни корневой [README.md](../README.md) только про продукт (в этой RU-копии README описывает харнесс — в продукте замени или вынеси).
3. Заполни [shared/stack.md](shared/stack.md), когда появятся команды.
4. Опциональный MCP: держи [mcp.json](mcp.json) пустым, пока не нужен; включай servers через сниппет в [shared/mcp-tools.md](shared/mcp-tools.md) (пин версий; только `${env:NAME}`).
5. Старт: `/new-case` + бриф → OUTBOX analyst. Дальше `/continue` / role skills по OUTBOX (`role-design`, когда назначен).

## День за днём

- Карта: [INDEX.md](INDEX.md)
- Оркестратор: [orchestrator/AGENTS.md](orchestrator/AGENTS.md)
- Принципы: [shared/harness-principles.md](shared/harness-principles.md)
- Golden demo: [orchestrator/cases/current/](orchestrator/cases/current/)
- Visual fidelity: разложи [refs/](orchestrator/cases/current/refs/) + `_index.md` → design hop → pack под [design/](orchestrator/cases/current/design/) → eng/qa потребляют pack

## Conventions

- Живут под `modules/<role>/conventions/` с **role prefixes** (`eng-*`, `qa-*`, `sec-*`, `analyst-*`, `design-*`).
- Модули читают **только свои**; conventions **никогда** не едут через OUTBOX.
- Поле CASE/FEATURE `surfaces: []` ⊂ {web, desktop, bots} гейтит файлы `*-web|desktop|bots`.
- Domain-файлы (`eng-db|network|io`) открываются только когда пакет трогает этот домен.
- `eng-ui` грузится только когда CASE `design_status=done`.
- Runners: `shared/stack.md` (разрешённый shared read — не convention relay).
- Политика MCP: `shared/mcp-tools.md` (разрешённый shared read; gate ≠ enabled server).
- eng / sec / qa / design держат разные углы — без copy-paste канона.

## Редактирование этого шаблона

Читай [shared/harness-principles.md](shared/harness-principles.md) и [rules/harness-edit.mdc](rules/harness-edit.mdc).

- Soft: process одного модуля; prefixed convention-правки в owning module + INDEX; MCP server без секретов + строка в mcp-tools.md.
- Hard: conventions в shared/overlays; универсальные conventions; unprefixed коллизии; cross-role copy; convention relay; surfaces вне web/desktop/bots без human; пустые stubs; fat root AGENTS; peer-handoff; секреты в mcp.json; `@latest` MCP по умолчанию; always-on eval/XSS MCP; add/remove modules / FSM без human hard.
- Лог в [shared/harness-changelog.md](shared/harness-changelog.md).

## Ручной аудит

| Check | Result |
|-------|--------|
| raw intake → qa OUTBOX? | NO |
| process вне `.cursor/`? | NO |
| root AGENTS thin? | YES |
| conventions local + prefixed? | YES |
| префикс `design-*` + design module? | YES |
| design = stage hop, не work_package? | YES |
| analyst ≠ visual extraction? | YES |
| eng-ui только когда design_status=done? | YES |
| политика design_skip задокументирована? | YES |
| rework_target на qa fail? | YES |
| гейт `surfaces[]`? | YES |
| eng-test ≠ qa-test? | YES |
| qa-desktop присутствует? | YES |
| shared/stack OK для runners? | YES |
| mcp-tools shared read? | YES |
| секреты в mcp.json? | NO |
| default mcpServers empty? | YES |
| convention OUTBOX relay? | NO |
| golden design_skip + design_status=skipped? | YES |
