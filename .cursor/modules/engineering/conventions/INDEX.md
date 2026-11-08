# Engineering conventions

**Who reads:** engineering only.

## Core (always)

| File | When |
|------|------|
| [eng-development.md](eng-development.md) | Any code change |
| [eng-test.md](eng-test.md) | Writing/running tests at build |
| [eng-tooling.md](eng-tooling.md) | Invoking build/test commands |
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
| [eng-ui.md](eng-ui.md) | design pack SoR — do **not** load when skipped/not_applicable |

Also honor FEATURE (Security must) + package acceptance + design pack paths when done. Never read foreign conventions. Runners → `shared/stack.md`.
