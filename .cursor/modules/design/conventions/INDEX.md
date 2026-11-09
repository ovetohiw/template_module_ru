# Design conventions

**Кто читает:** только design. Output → design pack + FEATURE.design + INBOX (не convention files).

## Core

| File | When |
|------|------|
| [design-refs.md](design-refs.md) | Каждый design synthesize |

## Surface (only if id ∈ CASE/FEATURE `surfaces[]`)

| File | Surface |
|------|---------|
| [design-web.md](design-web.md) | web |
| [design-desktop.md](design-desktop.md) | desktop |

Пустой `surfaces` / bots-only без GUI design hop → модуль не должен запускаться (`design_status=not_applicable`).
