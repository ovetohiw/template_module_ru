# work_package schema

Analyst `spec` payload must include `work_packages[]`:

```text
id:                      # unique string
layer:                   # allowlist only (below)
goal:                    # one clear outcome
depends_on: []           # other package ids
acceptance: []           # observable checks
artifacts_expected: []   # paths or artifact kinds
constraints: []          # optional
```

## Rules

- `layer` allowlist: **`security` | `implementation` | `verification` only**
- `design`, `requirements`, `acceptance` are stage/envelope hops — **never** `work_package.layer`
- no `.cursor/modules/...` paths
- deps must exist and be acyclic
- `verification` must depend on `implementation` (default)
- when CASE `design_status=done`: every `implementation` package must list design pack path in `artifacts_expected` or `constraints`
