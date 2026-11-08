# Scenario: register and login

## Happy path

1. Open register form; submit valid email+password.
2. System creates user; session authenticated.
3. Logout; login with same credentials succeeds.

## Failures

- Duplicate email → visible error; no session.
- Invalid credentials → visible error; no session.
