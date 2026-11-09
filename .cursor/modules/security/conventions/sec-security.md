# sec-security

**Кто читает:** security. **Кто не читает:** eng/qa (потребляют FEATURE must).

## Must

- Без secrets в repo, chat, FEATURE, evidence — только placeholders.
- AuthN на trusted side; passwords как strong hashes (не reversible storage).
- AuthZ server-side; UI hide ≠ authorization.
- Пиши blocking items в FEATURE Security must[] (M1…); should[] для non-blocking.
- `blocked`, если ambiguity ослабит authz/secrets — без guessed pass.
- Client input untrusted для security decisions.

## Should

- Язык minimal privilege; session lifetime/revocation, когда auth в scope.

## Forbidden

- Product code; правка conventions других модулей; relay conventions через OUTBOX; ослабление must ради зелёного статуса.
