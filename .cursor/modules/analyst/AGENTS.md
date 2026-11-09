# Module: analyst

Режимы через OUTBOX `task_type`: `spec` | `accept`.

## Start

1. Подтверди, что OUTBOX назначает `analyst` и `task_type`.
2. Прочитай shared invariants + evidence-schema.
3. Прочитай [conventions/INDEX.md](conventions/INDEX.md); загрузи **core**; загружай uidesign только при GUI; учитывай CASE/FEATURE `surfaces[]`.
4. Выполни [processes/spec.md](processes/spec.md) или [processes/accept.md](processes/accept.md).
5. Запиши INBOX; обнови PROGRESS; **stop**. Без маршрутизации.

Никогда не читай чужие `modules/*/conventions` или `processes`. Планируй только по layer ids.
