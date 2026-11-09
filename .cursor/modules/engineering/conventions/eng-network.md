# eng-network

**Кто читает:** engineering, когда package затрагивает network I/O.

## Must

- Явные timeouts на outbound calls; bounded retries с backoff; без infinite retry.
- Validate/sanitize данных на границах trust.
- TLS для внешнего sensitive traffic, если FEATURE не waives с risk note.
- Не логируй Authorization headers, tokens или полные secrets.

## Should

- Idempotent clients для retried mutating calls, где возможно.

## Forbidden

- Глотать network errors как success; доверять peer без auth, когда auth обязателен.
