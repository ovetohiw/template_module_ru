# Process: accept

## Do

1. Read [../conventions/INDEX.md](../conventions/INDEX.md) → analyst-docs.
2. Read FEATURE, evidence, handoffs, verification findings.
3. Check each acceptance criterion against evidence rows.
4. Record gates; fail if summary-only or missing qa-owned evidence where required.
5. Sync behavior or `unchanged[]` + reason.

## Do not

- Code fixes; self-close without evidence; weaken criteria.

## Out

INBOX `pass` → may close; `fail` → orchestrator rework.
