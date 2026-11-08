# Analyst conventions

**Who reads:** analyst only. Never ship via OUTBOX.

## Core (always)

| File | When |
|------|------|
| [analyst-docs.md](analyst-docs.md) | FEATURE, behavior, accept docs sync |

## Conditional

| File | When |
|------|------|
| [analyst-uidesign.md](analyst-uidesign.md) | GUI in scope (`surfaces` includes web/desktop, or UI acceptance) |

Bots/desktop **without** rich GUI: put UX in FEATURE acceptance; do not force uidesign.

Load gate: `surfaces` from CASE/FEATURE (`web` \| `desktop` \| `bots`).
