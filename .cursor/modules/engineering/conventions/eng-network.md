# eng-network

**Who reads:** engineering when package touches network I/O.

## Must

- Explicit timeouts on outbound calls; bounded retries with backoff; no infinite retry.
- Validate/sanitize data crossing trust boundaries.
- TLS for external sensitive traffic unless FEATURE waives with risk note.
- Do not log Authorization headers, tokens, or full secrets.

## Should

- Idempotent clients for retried mutating calls where feasible.

## Forbidden

- Swallowing network errors as success; trusting peer without auth when required.
