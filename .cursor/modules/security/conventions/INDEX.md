# Security conventions

**Кто читает:** только security. Output → FEATURE Security section + INBOX (не convention files).

## Core

| File | When |
|------|------|
| [sec-security.md](sec-security.md) | Каждый security review |

## Surface (only if id ∈ CASE/FEATURE `surfaces[]`)

| File | Surface |
|------|---------|
| [sec-web.md](sec-web.md) | web |
| [sec-desktop.md](sec-desktop.md) | desktop |
| [sec-bots.md](sec-bots.md) | bots |

Пустой `surfaces` → только core.
