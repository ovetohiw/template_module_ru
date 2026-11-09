# Принципы харнесса (конституция)

Неизменяемы без human hard approval. Держи этот файл ≤1 экрана.

1. **Hub-and-spoke** — модули никогда не адресуют друг друга; нет `to_role` / `to_module`.
2. **Thin root** — корневой `AGENTS.md` только роутер; без how-to ролей.
3. **Process под `.cursor/`** — никогда не клади process-файлы в дерево продукта.
4. **Lifecycle gates** — запрещённые рёбра в `LIFECYCLE.md` остаются закрытыми.
5. **Изоляция сырого брифа** — user intake никогда не становится qa/engineering OUTBOX.
6. **Evidence before done** — без close только по summary; без self-close роли.
7. **Одна роль за сессию** — autonomy C только внутри стадий engineering.
8. **SoR matrix** — статус только в CASE / INBOX / OUTBOX / handoffs.log / role PROGRESS.
9. **Load isolation** — нет чужих `modules/*/processes` или `conventions`; conventions **role-prefixed** (`eng-*`/`qa-*`/`sec-*`/`analyst-*`/`design-*`), никогда не едут через OUTBOX; грузи **core** всегда, **domain** по триггеру пакета, **surface** только если id ∈ CASE/FEATURE `surfaces[]` (web|desktop|bots); `shared/stack.md`, `shared/mcp-tools.md`, `invariants`, `evidence-schema` — разрешённые shared reads (не convention relay).
10. **Contracts before prose** — новый layer/hop нуждается в schema под `orchestrator/contracts/`.
11. **Skills thin** — skills — точки входа; они не дублируют полный DoD.
12. **No always-load-all** — alwaysApply не должен грузить каждый модуль.
13. **MCP tools** — декларации в проектном `.cursor/mcp.json`; секреты только через `${env:NAME}`; MCP не security boundary; пини версии; least privilege; политика только в `shared/mcp-tools.md`.
