# Module: design

## Start

1. OUTBOX must assign `design`.
2. Read shared invariants.
3. Read [conventions/INDEX.md](conventions/INDEX.md): always [design-refs.md](conventions/design-refs.md); add design-web|desktop only if id ∈ CASE/FEATURE `surfaces[]`.
4. Run [processes/synthesize.md](processes/synthesize.md).
5. Write INBOX; update FEATURE.design; update PROGRESS; **stop**.

Never ship convention files via OUTBOX. Never read foreign conventions. Never edit `plan.md` / work_packages. Never write product code.
