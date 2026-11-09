# Шаблон модульного харнесса (RU)

Копия шаблона `template_module` с правилами на русском. Это **не** README продукта — здесь описано, как пользоваться пайплайном агентов (оркестратор + роли).

Карта файлов: [`.cursor/INDEX.md`](.cursor/INDEX.md)  
Человеческий bootstrap: [`.cursor/TEMPLATE.md`](.cursor/TEMPLATE.md)

---

## Что это

Hub-and-spoke харнесс под Cursor: один **оркестратор** ведёт кейс, а роли (**analyst**, **design**, **security**, **engineering**, **qa**) работают только по брифу из `OUTBOX` и отвечают только через `INBOX`. Модули **не** пишут друг другу.

Процесс живёт только в `.cursor/`. Код продукта — снаружи.

```text
человек
  └─ /new-case | /continue | role-*
       └─ оркестратор (CASE / OUTBOX / INBOX / PROGRESS)
            ├─ analyst (spec / accept)
            ├─ design
            ├─ security
            ├─ engineering
            └─ qa
```

---

## Быстрый старт

1. Скопируйте папку в репозиторий продукта (или работайте из этой копии).
2. В реальном продукте **удалите** маркер [`.cursor/SCAFFOLD`](.cursor/SCAFFOLD), если он есть (иначе после `closed` кейс может сбрасываться).
3. Заполните [`.cursor/shared/stack.md`](.cursor/shared/stack.md) командами verify/run, когда стек известен.
4. MCP по желанию: [`.cursor/mcp.json`](.cursor/mcp.json) + политика [`.cursor/shared/mcp-tools.md`](.cursor/shared/mcp-tools.md).
5. В чате Cursor:
   - `/new-case` + бриф → оркестратор открывает кейс и выдаёт OUTBOX на analyst;
   - дальше по подсказке: `role-analyst` / `role-design` / `role-security` / `role-engineering` / `role-qa`;
   - `/continue` — только маршрутизация оркестратора по файлам (без угадывания роли из чата).

**Важно:** после DoD модуля в том же ходе не стартует соседняя роль. Один ход — одна роль (или один ход оркестратора).

---

## День за днём (как задумано)

| Шаг | Кто | Что делает |
|-----|-----|------------|
| 1 | человек | `/new-case` + сырой бриф |
| 2 | оркестратор | CASE → `analysis`, OUTBOX → analyst `spec` |
| 3 | analyst | нормализует FEATURE, behavior, `work_packages[]` → INBOX |
| 4 | оркестратор | если нужен дизайн → OUTBOX design; иначе `plan_review` |
| 5 | design (опц.) | refs → pack `TOKENS/SCREENS/COMPONENTS/DECISIONS` |
| 6 | оркестратор | `plan_review` (механические проверки плана) |
| 7 | execution | **последовательно**: security → implementation → verification |
| 8 | analyst `accept` | гейты закрытия кейса |
| 9 | оркестратор | `closed` или `blocked` |

Запрещено:

- сырой бриф сразу в OUTBOX для qa/engineering;
- параллельные OUTBOX (v1 — только serial);
- peer-handoff (`to_role` / «передай в разработку»);
- читать чужие `modules/*/processes` или `conventions`;
- тащить conventions через OUTBOX;
- invent `design_skip` из чата;
- `plan_review` при `design_status=pending`.

---

## Оркестратор: как взаимодействует

Оркестратор **не** пишет код и **не** выполняет how-to ролей. Он владеет жизненным циклом, маршрутизацией и SoR статуса кейса.

Канон:

- [`.cursor/orchestrator/AGENTS.md`](.cursor/orchestrator/AGENTS.md) — bootstrap каждого хода
- [`.cursor/orchestrator/LIFECYCLE.md`](.cursor/orchestrator/LIFECYCLE.md) — FSM
- [`.cursor/orchestrator/ROUTING.md`](.cursor/orchestrator/ROUTING.md) — слой → модуль + rework
- [`.cursor/orchestrator/LAYERS.md`](.cursor/orchestrator/LAYERS.md) — абстрактные слои
- [`.cursor/orchestrator/contracts/`](.cursor/orchestrator/contracts/) — схемы envelope / payloads

### Bootstrap каждого хода оркестратора

1. Прочитать `CASE.md`, `PROGRESS.md`, `OUTBOX.md`, `INBOX.md`.
2. Если `OUTBOX.status=pending` и задан `assigned_module` → **стоп**. Сказать человеку запустить соответствующий `role-*`. Не делать работу модуля.
3. Иначе если `INBOX.status=pending` → проверить envelope → дописать `handoffs.log.md` → применить LIFECYCLE+ROUTING → записать следующий OUTBOX или `blocked`/`closed` → обновить CASE+PROGRESS → **стоп**.
4. Иначе если stage=`intake` / нет активного кейса → ждать `/new-case`.
5. Никогда не invent следующую роль из чата — только CASE + contracts + ROUTING.

### Связка OUTBOX ↔ модуль ↔ INBOX

```text
оркестратор пишет OUTBOX (brief + поля)
        ↓
человек запускает role-* skill
        ↓
модуль читает OUTBOX, свои processes/conventions, артефакты кейса
        ↓
модуль пишет INBOX (envelope) + свой PROGRESS; OUTBOX → done
        ↓
человек /continue → оркестратор валидирует и маршрутизирует
```

Модули планируют по **layer id** (`requirements`, `design`, …), а не по именам папок.

### Soft vs hard

См. [`.cursor/shared/invariants.md`](.cursor/shared/invariants.md).

- **Soft** — решить внутри контракта и продолжить.
- **Hard** — стоп, blocker в PROGRESS, спросить человека.

---

## Файлы оркестратора и все поля

### 1. `CASE.md` — единый SoR активного кейса

| Поле | Смысл |
|------|--------|
| `case_id` | Уникальный id кейса |
| `stage` | Стадия FSM: `intake` \| `analysis` \| `design` \| `plan_review` \| `execution` \| `acceptance` \| `closed` \| `blocked` |
| `status` | Краткий статус кейса (`in_progress`, `done`, …) |
| `surfaces` | Поверхности продукта: подмножество `{web, desktop, bots}`. Гейтит `*-web\|desktop\|bots` conventions |
| `design_status` | `not_applicable` \| `skipped` \| `pending` \| `done` |
| `design_rework_from` | Откуда пришёл design-rework (напр. `verification`); иначе пусто |
| `assigned_module` | Кому сейчас выдан OUTBOX (зеркало маршрута) |
| `active_package_id` | Id текущего `work_package` в execution |
| `rounds` | Счётчики rework по классам фейлов (макс. 2 → `blocked`) |
| `blockers` | Список блокеров кейса |
| `waiver_verification_without_implementation` | Waiver: verification без implementation (по умолчанию `denied`) |
| `pointers` | Пути к FEATURE / plan / handoffs / evidence / behavior / refs / design |
| `raw_brief` | Сырой бриф человека (изолирован; не идёт в qa/eng OUTBOX) |

**`design_required`** (вычисляется, не всегда хранится отдельным полем):

```text
design_required =
  (web ∈ surfaces OR desktop ∈ surfaces)
  AND FEATURE.design_skip != true
```

`design_skip: true` без причины → invalid / hard.

### 2. `OUTBOX.md` — бриф оркестратора → **один** модуль

| Поле | Смысл |
|------|--------|
| `status` | `empty` \| `pending` \| `done` |
| `assigned_module` | `analyst` \| `design` \| `security` \| `engineering` \| `qa` |
| `layer` | Layer id hop’а: `requirements` \| `design` \| `security` \| `implementation` \| `verification` \| `acceptance` |
| `task_type` | Для analyst: `spec` \| `accept`; иначе вид пакета / n/a |
| `package_id` | Id work_package (в execution) |
| `case_id` | Связь с CASE |
| `brief` | Текстовый бриф задачи |
| `artifacts_in` | Входные пути артефактов |
| `written_at` | Время записи |

Доп. поля design-брифа (см. ROUTING):

| Поле | Смысл |
|------|--------|
| `feature_path` | Путь к FEATURE |
| `refs_index` | `cases/current/refs/_index.md` |
| `surfaces` | Поверхности для design conventions |
| `pack_dir` | Куда писать pack (`cases/current/design/`) |
| `rework` | `true` если design-rework |

В v1 одновременно активен **один** OUTBOX.

### 3. `INBOX.md` — ответ модуля → оркестратор (envelope)

| Поле | Смысл |
|------|--------|
| `status` | `empty` \| `pending` \| … |
| `case_id` | Id кейса |
| `from_layer` | Layer id отправителя (**не** имя папки модуля) |
| `task_type` | `spec` \| `accept` \| … |
| `verdict` | `pass` \| `fail` \| `blocked` \| `needs_input` |
| `summary` | 1–3 предложения; **не** SoR |
| `blockers` | Блокеры от модуля |
| `artifacts` | Пути артефактов |
| `payload` | Схема слоя (`contracts/layers/*`) |
| `written_at` | Время |

**Запрещено в ответе модуля:** `to_role`, `to_module`, `next_module`, проза «передай в …». Неполный envelope → hard, lifecycle не двигается.

### 4. `PROGRESS.md` (оркестратор) — заметки хода кейса

| Поле | Смысл |
|------|--------|
| `case_id` | Id |
| `stage` | Зеркало стадии |
| `next_step` | Что делать человеку/агенту дальше |
| `blocker` | Текущий hard-блокер |
| `last_hop` | Последний успешный/значимый hop |
| `notes` | Свободные заметки |
| `## Log` | Краткая история hop’ов |

У каждой роли свой `modules/<role>/PROGRESS.md` — только для работы роли, не заменяет CASE.

### 5. Артефакты кейса (`cases/current/`)

| Путь | Назначение |
|------|------------|
| `FEATURE.md` | Нормализованная фича (SoR требований + Security + design pointers) |
| `plan.md` | План / work_packages |
| `evidence.md` | Доказательства по schema |
| `behavior/` | Поведенческие спеки |
| `refs/` + `_index.md` | Визуальные референсы → экран |
| `design/` | Visual pack: TOKENS, SCREENS, COMPONENTS, DECISIONS |
| `handoffs.log.md` | Append-only история hop’ов |

### 6. Envelope / payloads по слоям

Общий каркас: [envelope.md](.cursor/orchestrator/contracts/envelope.md).

| Layer | Файл payload | Кратко |
|-------|--------------|--------|
| requirements | `contracts/layers/requirements.md` | goal, scope, FEATURE, work_packages |
| design | `design.md` | pack paths, screens, pack_complete, rework |
| security | `security.md` | must/should → FEATURE Security |
| implementation | `implementation.md` | package_id, changed_paths, how_to_verify |
| verification | `verification.md` | pass/fail, findings, evidence_rows, `rework_target` |
| acceptance | `acceptance.md` | gates, failed_criteria, evidence_complete |

### 7. `work_package` (планирует analyst)

Поля: `id`, `layer`, `goal`, `depends_on[]`, `acceptance[]`, `artifacts_expected[]`, `constraints[]`.

`layer` allowlist **только**: `security` \| `implementation` \| `verification`.  
`design` / `requirements` / `acceptance` — hop’ы стадий, **не** package.layer.

---

## Lifecycle (FSM)

```text
intake → analysis → design → plan_review → execution → acceptance → closed|blocked
```

`design` только если `design_required`. Иначе analysis → plan_review.

Execution packages (serial):

1. все ready `security`
2. все ready `implementation`
3. все ready `verification`
4. затем stage `acceptance`

Ready = зависимости удовлетворены. Один OUTBOX за раз.

### plan_review (механически, без продуктового суждения)

Проверяет allowlist слоёв, ацикличность deps, обязательные поля, связку verification→implementation, готовность design pack при `design_required`, и т.д. (полный список — LIFECYCLE.md).

Fail → OUTBOX обратно analyst `spec` с blockers.  
Pass → `execution`, первый ready package.

### Rework

На `fail`: `round++`, новый OUTBOX по `rework_target`:

| rework_target | Куда |
|---------------|------|
| `implementation` | engineering |
| `design` | design (`rework: true`, `design_rework_from=verification`) |
| `requirements` | analyst spec |

Макс. **2** раунда на класс фейла → иначе `blocked`.

---

## Привязка слой → модуль → skill

| Layer | Модуль | Skill |
|-------|--------|-------|
| requirements | analyst | `role-analyst` (`task_type=spec`) |
| design | design | `role-design` |
| security | security | `role-security` |
| implementation | engineering | `role-engineering` |
| verification | qa | `role-qa` |
| acceptance | analyst | `role-analyst` (`task_type=accept`) |

Skills тонкие: только вход. Полный DoD — в `modules/*/`.

---

## Conventions и surfaces

- Лежат в `modules/<role>/conventions/` с префиксами: `eng-*`, `qa-*`, `sec-*`, `analyst-*`, `design-*`.
- Модуль читает **только свои**.
- **Никогда** не едут через OUTBOX.
- `surfaces: [web|desktop|bots]` гейтит surface-файлы.
- Domain (`eng-db`, `eng-network`, `eng-io`) — только если пакет трогает домен.
- `eng-ui` — только при `design_status=done`.
- Runners: `shared/stack.md`. Политика MCP: `shared/mcp-tools.md`.

---

## Тонкости (частые ловушки)

1. **Оркестратор ≠ исполнитель.** Пока OUTBOX pending — запускайте `role-*`, не просите оркестратора «сделать за analyst».
2. **Один ход — одна роль.** После DoD модуля стоп; следующий hop — отдельный `/continue` или новый чат с оркестратором.
3. **Сырой бриф изолирован** в `raw_brief`. QA/eng работают от FEATURE/plan/package, не от «хочу сайт».
4. **Self-close запрещён:** одна сессия не должна и build-verify, и accept закрыть сама.
5. **Evidence:** «ok/passed» без command+result+artifact — невалидно ([evidence-schema.md](.cursor/shared/evidence-schema.md)).
6. **Design pack** — SoR для UI, когда `design_status=done`. Freestyle UI при готовом pack — hard.
7. **Не invent runners** вне `stack.md` / OUTBOX (MCP — не «придуманный runner», но и не замена stack).
8. **SCAFFOLD:** маркер шаблона; в боевом репо удалить. Иначе после `closed` возможен reset кейса.
9. **Правки харнесса** ≠ работа по кейсу. См. [harness-edit.mdc](.cursor/rules/harness-edit.mdc) и [harness-principles.md](.cursor/shared/harness-principles.md).
10. **Golden demo** в `cases/current/` — учебный закрытый кейс; для нового продукта сбросьте/замените артефакты.

---

## Skills (точки входа человека)

| Skill | Когда |
|-------|--------|
| `/new-case` | Нет активного кейса; есть бриф |
| `/continue` | Маршрутизация по файлам |
| `role-analyst` | OUTBOX → analyst |
| `role-design` | OUTBOX → design |
| `role-security` | OUTBOX → security |
| `role-engineering` | OUTBOX → engineering |
| `role-qa` | OUTBOX → qa (не сырой intake) |

---

## После клонирования в продукт

1. Удалить `.cursor/SCAFFOLD` (обязательно в реальном продукте).
2. Заполнить корневой README **продукта** (имя, run, deploy) — этот файл можно заменить или оставить рядом как `HARNESS.ru.md`.
3. Заполнить `shared/stack.md`.
4. MCP — по необходимости, без секретов в git (`${env:NAME}`).
5. `/new-case` + бриф.

Ручной аудит чеклиста — в [`.cursor/TEMPLATE.md`](.cursor/TEMPLATE.md).

---

## Глоссарий

См. [`.cursor/shared/glossary.md`](.cursor/shared/glossary.md). Ключевое:

- **case** — одна активная фича/задача оркестратора  
- **layer** — абстрактный слот capability  
- **module** — ролевой харнесс  
- **work_package** — единица плана analyst’а  
- **envelope** — структурированное сообщение module↔orchestrator  
- **soft / hard** — продолжить внутри контракта / стоп и спросить человека  

---
