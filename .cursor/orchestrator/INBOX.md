# INBOX

# Ответ модуля → оркестратор (envelope). См. contracts/envelope.md.

- status: empty
  # empty | pending | …
- case_id: golden-web-001
- from_layer: acceptance
  # layer id отправителя, не имя папки модуля
- task_type: accept
  # analyst: spec|accept; иначе n/a / вид пакета
- verdict: pass
  # pass | fail | blocked | needs_input
- summary: Golden acceptance gates passed; evidence complete for A1–A4 after one verification rework.
  # 1–3 предложения; не SoR
- blockers: []
- artifacts:
  - cases/current/evidence.md
  - cases/current/FEATURE.md
- payload: |
    gates: [G-evidence pass, G-pipeline pass, G-no-self-close pass]
    failed_criteria: []
    docs_updated: [behavior/]
    evidence_complete: true
  # schema по слою — contracts/layers/*
- written_at: 2026-11-08T12:15

# Запрещено: to_role / to_module / next_module / «передай в …»
