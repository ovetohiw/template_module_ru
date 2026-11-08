# FEATURE (active case)

- ID: golden-web-001
- Title: Simple site with DB, auth, UI
- Status: in_progress
- surfaces: [web]
- design_skip: true
- design_skip_reason: "golden protocol; no visual refs"
- design:
  refs_index: cases/current/refs/_index.md
  pack: cases/current/design/
  screens: []
- Goal: Users can register/login and see a basic authenticated UI backed by a database.
- Scope in:
  - Web UI shell
  - User auth (register/login/logout)
  - Persistent user store in DB
- Scope out:
  - Payments, OAuth social login, admin CMS, multi-tenant
- Acceptance:
  - [x] A1: Visitor can register with email+password and land in authenticated state
  - [x] A2: Registered user can log in again after session end
  - [x] A3: Authenticated UI shows a protected home view; anonymous user is redirected to login
  - [x] A4: User records persist in the configured database across restart
- Status note: golden demo closed with simulated product evidence (harness protocol real)
- Behavior paths:
  - cases/current/behavior/reg-login.md
  - cases/current/behavior/protected-home.md
- Security must:   # filled by security module into case SoR (not via convention relay)
  - [x] M1: Passwords stored as strong hashes; no plaintext in DB/repo
  - [x] M2: Session cookie httpOnly (or equivalent safe session storage decision recorded)
  - [x] M3: AuthZ on server; UI hide ≠ authorization
  - [x] M4: No secrets/tokens in repo, FEATURE, or evidence artifacts
- Security should:
  - [ ] S1: Short session TTL + explicit logout invalidates session
- Notes: Golden scenario for harness v1 (not a product implementation).
