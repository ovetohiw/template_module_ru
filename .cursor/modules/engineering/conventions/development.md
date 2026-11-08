# development (engineering)

**Who reads:** engineering only. **Who does not:** other modules.

## Must

- Stay inside current package / FEATURE scope; no drive-by refactors.
- Technologies only from `.cursor/shared/stack.md` (hard if missing choice).
- Diff only what the package needs; no unrelated format churn.
- Follow FEATURE Security must[] as case requirements (text in FEATURE), not foreign convention files.
- Do not claim feature-level done; return INBOX only.

## Should

- Match existing repo patterns before inventing structure.
- Use exec-plans for large packages; autonomy C = next stage only, never next role.

## Forbidden

- Inventing runners not in stack.md / OUTBOX.
- Committing secrets or real credentials.
- Starting qa/accept/security in this module session.
- Reading or copying other modules’ `conventions/`.
