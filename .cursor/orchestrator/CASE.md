# CASE

# SoR активного кейса. Поля протокола — на EN; комментарии — пояснения.

- case_id: golden-web-001
  # уникальный id кейса
- stage: closed
  # intake | analysis | design | plan_review | execution | acceptance | closed | blocked
- status: done
  # краткий статус (in_progress / done / …)
- surfaces: [web]
  # ⊂ {web, desktop, bots} — гейт surface-conventions
- design_status: skipped
  # not_applicable | skipped | pending | done
- design_rework_from:
  # откуда design-rework (напр. verification); иначе пусто
- assigned_module:
  # кому сейчас выдан OUTBOX
- active_package_id:
  # id текущего work_package в execution
- rounds: { verification_fail_wp-ver-1: 1 }
  # счётчики rework; макс. 2 на класс → blocked
- blockers: []
- waiver_verification_without_implementation: denied
  # waiver: verification без implementation (default denied)
- pointers:
  - feature: cases/current/FEATURE.md
  - plan: cases/current/plan.md
  - handoffs: cases/current/handoffs.log.md
  - evidence: cases/current/evidence.md
  - behavior: cases/current/behavior/
  - refs: cases/current/refs/
  - design: cases/current/design/
- raw_brief: "хочу чтобы был сайт и у него будет бд, авторизация, должен быть UI"
  # сырой бриф человека; изолирован от qa/eng OUTBOX
