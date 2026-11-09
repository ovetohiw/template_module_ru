# Engineering conventions

**Кто читает:** только engineering.

## Core (always)

| File | When |
|------|------|
| [eng-development.md](eng-development.md) | Любое изменение кода |
| [eng-test.md](eng-test.md) | Написание/запуск tests на build |
| [eng-tooling.md](eng-tooling.md) | Вызов команд build/test |
| [eng-config.md](eng-config.md) | Config/env/defaults |

## Domain (open only if package touches)

| File | Trigger |
|------|---------|
| [eng-db.md](eng-db.md) | DB/persistence/migrations |
| [eng-network.md](eng-network.md) | HTTP/RPC/outbound clients |
| [eng-io.md](eng-io.md) | Files, uploads, paths |

## Surface (only if id ∈ CASE/FEATURE `surfaces[]`)

| File | Surface |
|------|---------|
| [eng-web.md](eng-web.md) | web |
| [eng-desktop.md](eng-desktop.md) | desktop |
| [eng-bots.md](eng-bots.md) | bots |

## Visual pack (only if CASE `design_status=done`)

| File | When |
|------|------|
| [eng-ui.md](eng-ui.md) | design pack SoR — **не** загружай при skipped/not_applicable |

Также соблюдай FEATURE (Security must) + package acceptance + пути design pack при done. Никогда не читай чужие conventions. Runners → `shared/stack.md`.
