# Analyst conventions

**Who reads:** analyst module only.  
**Who does not:** security, engineering, qa (they use FEATURE/case artifacts + own conventions).

| File | Open when |
|------|-----------|
| [docs.md](docs.md) | Writing/updating FEATURE, behavior under `cases/current/behavior/`, accept docs sync |
| [uidesign.md](uidesign.md) | FEATURE/UI in scope; UI acceptance or behavior touches screens |

Never send these files (or copies) via OUTBOX. Put UI/product rules into FEATURE / work_packages as case text.
