# Lifecycle

```text
intake → analysis → design → plan_review → execution → acceptance → closed|blocked
```

Стадия `design` запускается только когда `design_required` (см. ROUTING). Иначе analysis → plan_review.

Пакеты execution (serial): `security` → `implementation` → `verification`.

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

| design_status | Когда |
|---------------|------|
| `not_applicable` | нет web/desktop в surfaces |
| `skipped` | web\|desktop, но `design_skip: true` + непустая reason |
| `pending` | выдан design OUTBOX / synthesize или design-rework в полёте |
| `done` | design pass; pack DoD ok |

`design_skip: true` без reason → invalid / hard.

## Запрещённые рёбра

- `intake` → `design` / `verification` / `implementation` / `security` / `acceptance`
- `analysis` → `implementation` когда `design_required` и `design_status` ≠ `done`
- `design` → `execution` минуя `plan_review` (кроме пути design-rework → повторная выдача implementation; см. ROUTING)
- сырой бриф пользователя → qa или engineering OUTBOX
- module → module (peer hop)
- параллельный OUTBOX (v1)
- `plan_review` при `design_status=pending`

## Проверки plan_review (механические)

Pass только если всё истинно:

1. Каждый `work_package.layer` ∈ {security, implementation, verification}
2. Нет filesystem-путей модулей в пакетах
3. Ids в `depends_on` существуют; граф ацикличен
4. Каждый пакет `verification` зависит от пакета `implementation` (waiver по умолчанию: denied)
5. Обязательные поля непусты: `id`, `layer`, `goal`, `acceptance[]`, `artifacts_expected[]`
6. Envelope от analyst `task_type=spec` полный
7. Нет `work_package.layer == design`
8. Если `design_required`: `design_status==done`, FEATURE.design.pack задан, файлы pack TOKENS/SCREENS/COMPONENTS/DECISIONS существуют и непусты
9. Если `design_status==done`: **каждый** пакет `implementation` перечисляет путь design pack (`cases/current/design/` или FEATURE.design.pack) в `artifacts_expected` или `constraints`
10. Если `design_status==skipped`: FEATURE.design_skip_reason непустой
11. Если `design_status==pending`: **не** запускай plan_review (Invalid)

Fail → OUTBOX обратно analyst `task_type=spec` со списком blockers.  
Не сбрасывай `design_status=done`, если blockers не говорят, что pack invalid.  
Pass → `execution`; первый ready package по serial order из ROUTING.

## Rework

На findings с `fail`: `round++`, повторная выдача OUTBOX по `rework_target` (ROUTING). Макс. **2** раунда на класс фейла → иначе `blocked`.
