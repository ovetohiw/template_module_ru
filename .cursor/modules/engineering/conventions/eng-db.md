# eng-db

**Who reads:** engineering when package touches DB.

## Must

- Parameterized queries only — no string-concat SQL with user input.
- Migrations reversible or explicitly one-way with recorded risk.
- No production data in dev/test DBs by default.
- AuthZ and tenancy enforced in data access, not only UI.

## Should

- Transactions around multi-step writes that must be atomic.

## Forbidden

- Trusting client-supplied row ids without ownership checks.
