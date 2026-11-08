# sec-security

**Who reads:** security. **Who does not:** eng/qa (consume FEATURE must).

## Must

- No secrets in repo, chat, FEATURE, evidence — placeholders only.
- AuthN on trusted side; passwords as strong hashes (not reversible storage).
- AuthZ server-side; UI hide ≠ authorization.
- Write blocking items to FEATURE Security must[] (M1…); should[] for non-blocking.
- `blocked` if ambiguity would weaken authz/secrets — no guessed pass.
- Client input untrusted for security decisions.

## Should

- Minimal privilege language; session lifetime/revocation when auth in scope.

## Forbidden

- Product code; editing other modules’ conventions; OUTBOX convention relay; weakening must to force green.
