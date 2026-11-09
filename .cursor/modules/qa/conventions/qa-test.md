# qa-test

**Кто читает:** qa (независимое verify). **Кто не читает:** engineering (eng-test).

## Must

- Verify FEATURE acceptance + behavior независимо; evidence rows по `shared/evidence-schema.md` (`role=qa`).
- Runners только из `shared/stack.md` или OUTBOX; пустые слоты → явная note, без изобретённого runner.
- Optional MCP evidence tools только по `shared/mcp-tools.md` (не runner-slot; не замена `stack.md`). Нет MCP ≠ skip verify — fallback на stack/manual; не изобретай success. Укажи source в `command_or_action` (`mcp:…` / `stack:…` / `manual`).
- Предпочитай behavioral/e2e checks для critical paths; не принимай unit-on-mocks как единственное proof user path.
- Failures → findings[] (id, severity); verdict `fail` — не назначай eng сам.
- Один code-read ≠ pass, когда OUTBOX требует run.
- Без secrets/PII в evidence artifacts.

## Should

- Трассируй к behavior files; одна ясная причина failure на finding.
- Где есть multi-user resources, пытайся cross-user access (IDOR pattern).

## Forbidden

- Raw intake как brief; pass только по summary; ослабление asserts; чужие conventions; закрытие accept/case из qa.
