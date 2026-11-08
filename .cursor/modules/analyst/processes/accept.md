# Process: accept

## Do

1. Read [../conventions/INDEX.md](../conventions/INDEX.md) (docs.md for sync rules).
2. Read FEATURE, evidence.md, handoffs.log, verification findings.
3. Check each acceptance criterion against evidence rows (evidence-schema).
4. Record gates; fail if summary-only or missing QA-owned rows where required.
5. Sync behavior docs or state `unchanged[]` + reason.

## Do not

- Implement code fixes
- Self-close without evidence
- Weaken criteria to force pass

## Out

INBOX `pass` → orchestrator may close; `fail` → rework classification by orchestrator.
