# eng-web

**Кто читает:** engineering, когда `web` ∈ surfaces. Угол build.

## Must

- Enforce authz на server для sensitive routes; никогда не полагайся только на hidden UI.
- Validate inputs; parameterized data access; безопасные error bodies (без stacks/tokens).
- Cookie auth: httpOnly; Secure в prod; deliberate SameSite.
- Не шипь `Access-Control-Allow-Origin: *` с credentials.
- CSRF defense (или эквивалент) для cookie-authenticated state changes.

## Should

- Rate-limit login и других abuse-prone endpoints.

## Forbidden

- Копирование sec-web/qa-web как этот файл; client-only authz.
