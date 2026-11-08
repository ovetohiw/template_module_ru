# work_package schema

Analyst `spec` payload must include `work_packages[]`:

```text
id:                      # unique string
layer:                   # from LAYERS.md
goal:                    # one clear outcome
depends_on: []           # other package ids
acceptance: []           # observable checks
artifacts_expected: []   # paths or artifact kinds
constraints: []          # optional
```

## Rules

- `layer` must be an abstract layer id
- no `.cursor/modules/...` paths
- deps must exist and be acyclic
- `verification` must depend on `implementation` (default)
