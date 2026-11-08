# Glossary

| Term | Meaning |
|------|---------|
| case | One active feature/task owned by orchestrator |
| layer | Abstract capability slot (`requirements`, `security`, …) |
| module | Role harness under `.cursor/modules/<name>/` |
| work_package | Analyst-planned unit bound to one layer |
| envelope | Structured module↔orchestrator message |
| OUTBOX | Current brief from orchestrator to one module |
| INBOX | Current result from module to orchestrator |
| handoffs.log | Append-only hop history for the case |
| plan_review | Mechanical validation of work_packages |
| task_type | Analyst mode: `spec` or `accept` |
| autonomy C | Engineering may continue next *stage* after green DoD; never next *role* |
| soft | Decide inside contract and continue |
| hard | Stop; write blocker; ask human |
