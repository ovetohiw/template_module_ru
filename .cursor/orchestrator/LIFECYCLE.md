# Lifecycle

```text
intake → analysis → design → plan_review → execution → acceptance → closed|blocked
```

`design` stage runs only when `design_required` (see ROUTING). Otherwise analysis → plan_review.

Execution packages (serial): `security` → `implementation` → `verification`.

## Stage vs package

| Kind | Ids | work_package? |
|------|-----|---------------|
| Lifecycle stages | intake, analysis, design, plan_review, execution, acceptance, closed, blocked | no |
| Envelope layers (hop) | requirements, design, security, implementation, verification, acceptance | hop only |
| work_package.layer allowlist | security, implementation, verification | yes |

## design_required / design_status

```text
design_required =
  (web ∈ surfaces OR desktop ∈ surfaces)
  AND FEATURE.design_skip != true
```

| design_status | When |
|---------------|------|
| `not_applicable` | no web/desktop in surfaces |
| `skipped` | web\|desktop but `design_skip: true` + non-empty reason |
| `pending` | design OUTBOX issued / synthesize or design-rework in flight |
| `done` | design pass; pack DoD ok |

`design_skip: true` without reason → invalid / hard.

## Forbidden edges

- `intake` → `design` / `verification` / `implementation` / `security` / `acceptance`
- `analysis` → `implementation` when `design_required` and `design_status` ≠ `done`
- `design` → `execution` skipping `plan_review` (except design-rework path → re-issue implementation; see ROUTING)
- raw user brief → qa or engineering OUTBOX
- module → module (peer hop)
- parallel OUTBOX (v1)
- `plan_review` while `design_status=pending`

## plan_review checks (mechanical)

Pass only if all true:

1. Every `work_package.layer` ∈ {security, implementation, verification}
2. No module filesystem paths in packages
3. `depends_on` ids exist; graph acyclic
4. Each `verification` package depends on an `implementation` package (waiver default: denied)
5. Required fields non-empty: `id`, `layer`, `goal`, `acceptance[]`, `artifacts_expected[]`
6. Envelope from analyst `task_type=spec` is complete
7. No `work_package.layer == design`
8. If `design_required`: `design_status==done`, FEATURE.design.pack set, pack files TOKENS/SCREENS/COMPONENTS/DECISIONS exist and non-empty
9. If `design_status==done`: **every** `implementation` package lists design pack path (`cases/current/design/` or FEATURE.design.pack) in `artifacts_expected` or `constraints`
10. If `design_status==skipped`: FEATURE.design_skip_reason non-empty
11. If `design_status==pending`: do **not** run plan_review (Invalid)

Fail → OUTBOX back to analyst `task_type=spec` with blocker list.  
Do not clear `design_status=done` unless blockers say pack invalid.  
Pass → `execution`; first ready package by ROUTING serial order.

## Rework

On `fail` findings: `round++`, re-issue OUTBOX per `rework_target` (ROUTING). Max **2** rounds per fail class → else `blocked`.
