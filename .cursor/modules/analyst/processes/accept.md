# Process: accept

## Do

1. Прочитай [../conventions/INDEX.md](../conventions/INDEX.md) → analyst-docs.
2. Прочитай FEATURE, evidence, handoffs, verification findings.
3. Проверь каждый acceptance criterion по evidence rows.
4. Зафиксируй gates; fail, если только summary или нет обязательных qa-owned evidence.
5. Синхронизируй behavior или `unchanged[]` + reason.

## Do not

- Правки кода; самозакрытие без evidence; ослабление criteria.

## Out

INBOX `pass` → можно закрыть; `fail` → orchestrator rework.
