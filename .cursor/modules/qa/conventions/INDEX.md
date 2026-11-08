# QA conventions

**Who reads:** qa only. Brief = verification package + case artifacts — never raw intake alone.

## Core

| File | When |
|------|------|
| [qa-test.md](qa-test.md) | Every verification package |

## Surface (only if id ∈ CASE/FEATURE `surfaces[]`)

| File | Surface |
|------|---------|
| [qa-web.md](qa-web.md) | web |
| [qa-desktop.md](qa-desktop.md) | desktop |
| [qa-bots.md](qa-bots.md) | bots |

Empty `surfaces` → core only. Never read eng/security conventions.
