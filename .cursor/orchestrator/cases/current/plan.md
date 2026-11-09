# Plan (work_packages)

case_id: golden-web-001

## work_packages

### wp-sec-1
- layer: security
- goal: Определить must/should для auth-учётных данных, сессии и секретов БД
- depends_on: []
- acceptance:
  - must[] покрывает хранение паролей, session cookie, работу с секретами
- artifacts_expected:
  - security notes в payload INBOX
- constraints:
  - без plaintext-паролей

### wp-impl-1
- layer: implementation
- goal: Реализовать auth на БД + защищённую оболочку UI по FEATURE
- depends_on: [wp-sec-1]
- acceptance:
  - поведения A1–A4 существуют в приложении
- artifacts_expected:
  - пути кода, перечисленные в payload implementation
- constraints:
  - соблюдать security must[]

### wp-ver-1
- layer: verification
- goal: Независимо проверить A1–A4 со строками evidence
- depends_on: [wp-impl-1]
- acceptance:
  - строки evidence для A1–A4; findings при fail
- artifacts_expected:
  - обновления cases/current/evidence.md
- constraints:
  - не использовать сырой intake как единственный brief
