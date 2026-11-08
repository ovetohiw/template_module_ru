# Glossary

| Term | Meaning |
|------|---------|
| case | One active feature/task owned by orchestrator |
| layer | Abstract capability slot (`requirements`, `design`, `security`, …) |
| module | Role harness under `.cursor/modules/<name>/` |
| work_package | Analyst-planned unit; `layer` allowlist: security\|implementation\|verification |
| envelope | Structured module↔orchestrator message |
| OUTBOX | Current brief from orchestrator to one module |
| INBOX | Current result from module to orchestrator |
| handoffs.log | Append-only hop history for the case |
| plan_review | Mechanical validation of work_packages (+ design_status gates) |
| task_type | Analyst mode: `spec` or `accept` |
| design stage | Lifecycle hop after analysis; refs → visual pack; not a work_package |
| design_status | `not_applicable` \| `skipped` \| `pending` \| `done` |
| design_skip | FEATURE flag to skip design hop (reason required); policy in analyst-uidesign |
| design pack | `cases/current/design/` TOKENS/SCREENS/COMPONENTS/DECISIONS — eng/qa SoR |
| refs index | `cases/current/refs/_index.md` — screen → primary_ref map |
| rework_target | On qa fail: `implementation` \| `design` \| `requirements` |
| autonomy C | Engineering may continue next *stage* after green DoD; never next *role* |
| soft | Decide inside contract and continue |
| hard | Stop; write blocker; ask human |

## Stage vs package

| Kind | Ids | work_package? |
|------|-----|---------------|
| Lifecycle stages | intake, analysis, design, plan_review, execution, acceptance, closed, blocked | no |
| Envelope layers | requirements, design, security, implementation, verification, acceptance | hop |
| Package layers | security, implementation, verification | yes |
