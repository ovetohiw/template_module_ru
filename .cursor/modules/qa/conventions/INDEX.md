# QA conventions

**Кто читает:** только qa. Brief = verification package + case artifacts — никогда только raw intake.

## Core

| File | When |
|------|------|
| [qa-test.md](qa-test.md) | Каждый verification package |

## Surface (only if id ∈ CASE/FEATURE `surfaces[]`)

| File | Surface |
|------|---------|
| [qa-web.md](qa-web.md) | web |
| [qa-desktop.md](qa-desktop.md) | desktop |
| [qa-bots.md](qa-bots.md) | bots |

Пустой `surfaces` → только core. Никогда не читай eng/security conventions.
