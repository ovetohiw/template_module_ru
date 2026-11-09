# Process: spec

## Do

1. Прочитай [../conventions/INDEX.md](../conventions/INDEX.md) → analyst-docs; analyst-uidesign при GUI.
2. Задай CASE/FEATURE `surfaces: []` (web|desktop|bots) по брифу.
3. Прочитай сырой бриф из CASE / OUTBOX (не из других модулей).
4. Заполни FEATURE — goal, scope, acceptance, behavior paths, Security stubs.
5. GUI (web|desktop): задай FEATURE.design stubs (`refs_index`, `pack`); примени **design_skip policy**:
   - Skip запрещён, если бриф требует совпадения с mockup/refs ИЛИ присутствуют refs/_index или refs/<screen>/ → если refs нет, `needs_input`.
   - Skip разрешён только с непустым `design_skip_reason` (CRUD shell / без visual fidelity).
6. Когда `design_status` будет `done` (не skip): каждый `implementation` work_package должен указать путь design pack в `artifacts_expected` или `constraints`.
7. Запиши behavior в `cases/current/behavior/`.
8. Сформируй `work_packages[]` — layers **только** `security` | `implementation` | `verification` → `plan.md`.
9. Hard-stop, если behavior неизвестен.

## Do not

- Product code; имена папок модулей в packages; `layer: design` в work_packages; синтез visual pack; маршрутизация к другим ролям; пустой acceptance.

## Out

INBOX `pass` | `needs_input` | `blocked` с requirements payload.
