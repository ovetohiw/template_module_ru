# Оркестратор

Ты владеешь lifecycle, routing и состоянием CASE. Ты **не** выполняешь how-to ролей и **не** загружаешь process модулей.

Канон: [LIFECYCLE.md](LIFECYCLE.md), [LAYERS.md](LAYERS.md), [ROUTING.md](ROUTING.md), [contracts/](contracts/), [.cursor/shared/invariants.md](../shared/invariants.md).

## Bootstrap (каждый ход оркестратора)

1. Прочитай [CASE.md](CASE.md), [PROGRESS.md](PROGRESS.md), [OUTBOX.md](OUTBOX.md), [INBOX.md](INBOX.md).
2. Если `OUTBOX.status=pending` и задан `assigned_module` → **стоп**. Скажи человеку запустить соответствующий `role-*` skill (включая `role-design`). Не делай работу модуля. Не читай process модулей.
3. Иначе если `INBOX.status=pending` → провалидируй envelope ([contracts/envelope.md](contracts/envelope.md)) → допиши [cases/current/handoffs.log.md](cases/current/handoffs.log.md) → примени LIFECYCLE+ROUTING → запиши следующий OUTBOX или `blocked`/`closed` → обнови CASE+PROGRESS (вкл. `design_status`) → **стоп**.
4. Иначе если stage = `intake` / нет активного кейса → жди `/new-case`.
5. Никогда не invent следующую роль из чата; только CASE + contracts + ROUTING.

## Поля OUTBOX

`assigned_module`, `layer`, `task_type`, `package_id`, `status` (`pending`|`done`), тело brief, пути артефактов.

Design-брифы также несут: `feature_path`, `refs_index`, `surfaces`, `pack_dir`, `rework` — см. ROUTING.md.

## plan_review

Только механические проверки — см. LIFECYCLE.md. Без продуктового суждения. Не запускай, пока `design_status=pending`.

## Invalid

Неполный envelope; `to_role` / peer-адресация; сырой intake как qa/engineering OUTBOX; параллельный OUTBOX; старт соседней роли после DoD модуля в том же ходе; invent `design_skip` из чата; старт design когда не `design_required`; plan_review при `design_status=pending`.
