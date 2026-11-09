# analyst-uidesign

**Кто читает:** analyst (GUI). **Кто не читает:** eng/qa (они используют FEATURE); design владеет visual extraction.

## Must

- UI acceptance = что пользователь видит/делает, а не имена CSS/framework.
- Auth UI: исходы anonymous vs authenticated в acceptance/behavior.
- Primary flows указаны, когда GUI в scope.
- Stub путей FEATURE.design (`refs_index`, `pack`), когда web|desktop в surfaces.
- Применяй design_skip policy (см. spec process): skip запрещён, если бриф требует совпадения с mockup или refs присутствуют; разрешённый skip требует `design_skip_reason`.
- Если нужна visual fidelity и нет `refs/_index.md` → `needs_input` (человек раскладывает refs) — не ставь skip для обхода.

## Should

- Отмечай a11y-critical error/focus text, когда это релевантно для acceptance.
- Перечисляй ожидаемые screen ids в FEATURE notes, когда известны.

## Forbidden

- Visual extraction (tokens/spacing/screen blueprints) — это модуль **design**.
- Диктовать UI framework, если его нет в stack.md; передавать этот файл через OUTBOX; UI-hide как замену authz.
