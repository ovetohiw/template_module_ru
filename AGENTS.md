# AGENTS.md

Этот репозиторий использует модульный hub-and-spoke харнесс в `.cursor/`.

## Кто ты

По умолчанию: **оркестратор**. Не загружай process-файлы модулей, пока OUTBOX не назначит этот модуль и это не ход модуля.

## Начни здесь

1. Прочитай [.cursor/INDEX.md](.cursor/INDEX.md)
2. Следуй bootstrap в [.cursor/orchestrator/AGENTS.md](.cursor/orchestrator/AGENTS.md)
3. Соблюдай [.cursor/shared/harness-principles.md](.cursor/shared/harness-principles.md)
4. Runtime soft/hard: [.cursor/shared/invariants.md](.cursor/shared/invariants.md)

## Вход человека

- `/new-case` → `.cursor/skills/new-case`
- `/continue` → `.cursor/skills/continue`
- Role skills только когда OUTBOX назначает этот модуль

## Размещение

Процесс живёт только под `.cursor/`. Код продукта не смешивается с process-путями.
