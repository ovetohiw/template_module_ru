# Design conventions

**Who reads:** design only. Output → design pack + FEATURE.design + INBOX (not convention files).

## Core

| File | When |
|------|------|
| [design-refs.md](design-refs.md) | Every design synthesize |

## Surface (only if id ∈ CASE/FEATURE `surfaces[]`)

| File | Surface |
|------|---------|
| [design-web.md](design-web.md) | web |
| [design-desktop.md](design-desktop.md) | desktop |

Empty `surfaces` / bots-only without GUI design hop → module should not run (`design_status=not_applicable`).
