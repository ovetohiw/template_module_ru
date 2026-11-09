# qa-bots

**Кто читает:** qa, когда `bots` ∈ surfaces. Угол verify.

## Must

- Отклоняй requests без valid inbound secret (или документируй blocked environment).
- Replay/duplicate update не даёт double side effect (idempotency).
- Unauthorized callback/user не может выполнить privileged action.
- Bot token не появляется в logs/evidence, захваченных для run.

## Should

- Abuse: rapid repeated commands rate-limited, когда это в FEATURE.

## Forbidden

- Доверять только platform delivery без secret check, когда webhook mode в scope.
