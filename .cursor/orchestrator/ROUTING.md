# Routing

## Bind layer → module

| Layer | Путь модуля | Skill |
|-------|-------------|-------|
| requirements | `.cursor/modules/analyst` | role-analyst (`task_type=spec`) |
| design | `.cursor/modules/design` | role-design |
| security | `.cursor/modules/security` | role-security |
| implementation | `.cursor/modules/engineering` | role-engineering |
| verification | `.cursor/modules/qa` | role-qa |
| acceptance | `.cursor/modules/analyst` | role-analyst (`task_type=accept`) |

## Serial order (v1)

После plan_review pass выдавай пакеты по порядку:

1. все ready `security`
2. все ready `implementation`
3. все ready `verification`
4. затем stage `acceptance`

Ready = deps удовлетворены. Один OUTBOX за раз.

`design` **не** в этом serial-списке (stage-gate до plan_review, либо design-rework mid-execution).

## Classification (INBOX → next)

### Analyst spec pass (включая rework после plan_review fail)

Пересчитай `design_required` из FEATURE.surfaces + design_skip:

1. Если `design_required` И `design_status != done` → stage=`design`; `design_status=pending`; OUTBOX design
2. Иначе если `design_required` И `design_status == done` → plan_review
3. Иначе если web|desktop в surfaces И design_skip → `design_status=skipped`; plan_review
4. Иначе → `design_status=not_applicable`; plan_review

### Design

| Сигнал | Next |
|--------|------|
| design `pass` | `design_status=done`. Если `design_rework_from=verification`: очисти флаг; повторно выдай тот же implementation package; stage=`execution`. Иначе → plan_review |
| design `needs_input` / `blocked` | стоп; без plan_review; без impl |

### Plan review / execution / accept

| Сигнал | Next |
|--------|------|
| plan_review fail | analyst spec (blockers); держи `design_status=done`, если blockers не говорят, что pack invalid |
| plan_review pass | первый ready execution package |
| security `pass` | следующий ready package |
| security `blocked` | blocked / human |
| implementation `pass` | следующий ready package |
| verification `pass` | acceptance (когда все verification packages done) |
| verification `fail` | см. rework_target ниже |
| acceptance `pass` | closed |
| acceptance `fail` | rework → implementation (или requirements) |
| любой неполный envelope | hard; не продвигай |
| payload содержит `to_role` / peer address | invalid; hard |

### Verification fail → rework_target

Читай `findings[].rework_target` (по умолчанию `implementation`, если нет):

| rework_target | Next |
|---------------|------|
| `implementation` | OUTBOX engineering (как сейчас) |
| `design` | set `design_rework_from=verification`; stage=`design`; `design_status=pending`; OUTBOX design (`rework: true`) |
| `requirements` | OUTBOX analyst spec |

`round++` на класс фейла; макс. 2 → blocked.

## Поля design OUTBOX brief

```text
assigned_module: design
layer: design
status: pending
feature_path: cases/current/FEATURE.md
refs_index: cases/current/refs/_index.md
surfaces: []
pack_dir: cases/current/design/
rework: false|true
```

## Conventions

**Не** копируй и не ретранслируй `modules/*/conventions` через OUTBOX. Downstream-модули читают пути FEATURE / plan / evidence / design pack и **свои** role-prefixed conventions (гейтятся `surfaces[]`). Security должен жить в FEATURE после security hop. Design pack живёт под FEATURE.design после design hop. `shared/stack.md` разрешён для runners. `shared/mcp-tools.md` разрешён для политики MCP (не convention relay).
