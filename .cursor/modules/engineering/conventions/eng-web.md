# eng-web

**Who reads:** engineering when `web` ∈ surfaces. Build angle.

## Must

- Enforce authz on server for sensitive routes; never rely on hidden UI alone.
- Validate inputs; parameterized data access; safe error bodies (no stacks/tokens).
- Cookie auth: httpOnly; Secure in prod; deliberate SameSite.
- Do not ship `Access-Control-Allow-Origin: *` with credentials.
- CSRF defense (or equivalent) for cookie-authenticated state changes.

## Should

- Rate-limit login and other abuse-prone endpoints.

## Forbidden

- Copying sec-web/qa-web as this file; client-only authz.
