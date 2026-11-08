# Security conventions

**Who reads:** security only. Output → FEATURE Security section + INBOX (not convention files).

## Core

| File | When |
|------|------|
| [sec-security.md](sec-security.md) | Every security review |

## Surface (only if id ∈ CASE/FEATURE `surfaces[]`)

| File | Surface |
|------|---------|
| [sec-web.md](sec-web.md) | web |
| [sec-desktop.md](sec-desktop.md) | desktop |
| [sec-bots.md](sec-bots.md) | bots |

Empty `surfaces` → core only.
