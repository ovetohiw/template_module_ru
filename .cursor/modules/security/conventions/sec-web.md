# sec-web

**Who reads:** security when `web` ∈ surfaces. Review angle only.

## Must

- Require server authz on every sensitive HTTP action; flag IDOR risk (object id from client).
- Cookie sessions: httpOnly; Secure in prod; document SameSite decision.
- Reject `Access-Control-Allow-Origin: *` with credentials.
- Errors must not leak stack traces, tokens, or internal paths to clients.
- State-changing browser flows need CSRF defense or equivalent when cookie auth.

## Should

- Rate-limit auth endpoints called out in must/should when brute-force relevant.

## Forbidden

- Copying eng-web/qa-web text as this file’s canon; framework-specific dogma as must.
