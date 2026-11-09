# Analyst conventions

**Кто читает:** только analyst. Никогда не передавать через OUTBOX.

## Core (always)

| File | When |
|------|------|
| [analyst-docs.md](analyst-docs.md) | FEATURE, behavior, синхронизация accept docs |

## Conditional

| File | When |
|------|------|
| [analyst-uidesign.md](analyst-uidesign.md) | GUI в scope (`surfaces` включает web/desktop, или UI acceptance) |

Bots/desktop **без** rich GUI: UX описывай в FEATURE acceptance; не форсируй uidesign.

Load gate: `surfaces` из CASE/FEATURE (`web` \| `desktop` \| `bots`).
