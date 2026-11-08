# Plan (work_packages)

case_id: golden-web-001

## work_packages

### wp-sec-1
- layer: security
- goal: Define must/should for auth credentials, session, and DB secrets
- depends_on: []
- acceptance:
  - must[] covers password storage, session cookie, secret handling
- artifacts_expected:
  - security notes in INBOX payload
- constraints:
  - no plaintext passwords

### wp-impl-1
- layer: implementation
- goal: Implement DB-backed auth + protected UI shell per FEATURE
- depends_on: [wp-sec-1]
- acceptance:
  - A1–A4 behaviors exist in app
- artifacts_expected:
  - code paths listed in implementation payload
- constraints:
  - respect security must[]

### wp-ver-1
- layer: verification
- goal: Independently verify A1–A4 with evidence rows
- depends_on: [wp-impl-1]
- acceptance:
  - evidence rows for A1–A4; findings if fail
- artifacts_expected:
  - cases/current/evidence.md updates
- constraints:
  - do not use raw intake as sole brief
