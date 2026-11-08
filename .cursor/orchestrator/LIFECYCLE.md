# Lifecycle

```text
intake → analysis → plan_review → execution → acceptance → closed|blocked
```

Execution layers (serial): `security` → `implementation` → `verification`.

## Forbidden edges

- `intake` → `verification` / `implementation` / `security` / `acceptance`
- raw user brief → qa or engineering OUTBOX
- module → module (peer hop)
- parallel OUTBOX (v1)

## plan_review checks (mechanical)

Pass only if all true:

1. Every `work_package.layer` ∈ LAYERS.md
2. No module filesystem paths in packages
3. `depends_on` ids exist; graph acyclic
4. Each `verification` package depends on an `implementation` package (waiver default: denied)
5. Required fields non-empty: `id`, `layer`, `goal`, `acceptance[]`, `artifacts_expected[]`
6. Envelope from analyst `task_type=spec` is complete

Fail → OUTBOX back to analyst `task_type=spec` with blocker list.  
Pass → `execution`; first ready package by ROUTING serial order.

## Rework

On `fail` findings: `round++`, re-issue OUTBOX to target layer. Max **2** rounds per fail class → else `blocked`.
