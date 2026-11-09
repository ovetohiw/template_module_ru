# eng-db

**Кто читает:** engineering, когда package затрагивает DB.

## Must

- Только parameterized queries — без string-concat SQL с user input.
- Migrations обратимы или явно one-way с зафиксированным risk.
- Без production data в dev/test DBs по умолчанию.
- AuthZ и tenancy enforced в data access, а не только в UI.

## Should

- Transactions вокруг multi-step writes, которые должны быть atomic.

## Forbidden

- Доверять client-supplied row ids без ownership checks.
