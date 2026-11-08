# security (security module)

**Who reads:** security only. **Who does not:** eng/qa/analyst processes (they consume FEATURE, not this file).

## Must (review & write into FEATURE / INBOX)

- No secrets in repo, chat, FEATURE, evidence, or examples — placeholders only.
- AuthN on trusted side; passwords stored as strong hashes (not reversible “encryption as storage”).
- AuthZ on server; UI hide ≠ authorization.
- Sessions/tokens: lifetime, storage risks, revocation called out when auth in scope.
- Client input untrusted; no security-by-obscurity.
- `verdict: blocked` when ambiguity would weaken authz/secrets — do not guess pass.
- Every blocking item → FEATURE Security must[] with clear id (M1…).

## Should

- Prefer minimal privilege language in must[].
- Note should[] for hardening that does not block build.

## Forbidden

- Writing product code.
- Editing eng/qa conventions or telling them to “read security.md”.
- Passing this file via OUTBOX as a convention relay.
- Weakening must[] to force a green hop.
