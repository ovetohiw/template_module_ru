# Глоссарий

| Термин | Значение |
|--------|----------|
| case | Один активный feature/task под оркестратором |
| layer | Абстрактный слот capability (`requirements`, `design`, `security`, …) |
| module | Ролевой харнесс под `.cursor/modules/<name>/` |
| work_package | Единица плана analyst’а; allowlist `layer`: security\|implementation\|verification |
| envelope | Структурированное сообщение module↔orchestrator |
| OUTBOX | Текущий бриф оркестратора одному модулю |
| INBOX | Текущий результат модуля оркестратору |
| handoffs.log | Append-only история hop’ов кейса |
| plan_review | Механическая валидация work_packages (+ гейты design_status) |
| task_type | Режим analyst: `spec` или `accept` |
| design stage | Lifecycle hop после analysis; refs → visual pack; не work_package |
| design_status | `not_applicable` \| `skipped` \| `pending` \| `done` |
| design_skip | Флаг FEATURE пропустить design hop (reason обязателен); политика в analyst-uidesign |
| design pack | `cases/current/design/` TOKENS/SCREENS/COMPONENTS/DECISIONS — SoR для eng/qa |
| refs index | `cases/current/refs/_index.md` — карта screen → primary_ref |
| rework_target | На qa fail: `implementation` \| `design` \| `requirements` |
| autonomy C | Engineering может продолжить следующую *стадию* после green DoD; никогда следующую *роль* |
| soft | Реши внутри контракта и продолжай |
| hard | Стой; запиши blocker; спроси человека |

## Stage vs package

| Kind | Ids | work_package? |
|------|-----|---------------|
| Lifecycle stages | intake, analysis, design, plan_review, execution, acceptance, closed, blocked | no |
| Envelope layers | requirements, design, security, implementation, verification, acceptance | hop |
| Package layers | security, implementation, verification | yes |
