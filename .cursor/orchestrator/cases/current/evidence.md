# Evidence

Rows per [.cursor/shared/evidence-schema.md](../../../shared/evidence-schema.md).

| criterion | command_or_action | result | artifact | role | session |
|-----------|-------------------|--------|----------|------|---------|
| A1 | Manual/scripted register flow (simulated golden) | new user authenticated | behavior/reg-login.md | qa | 2026-11-08 |
| A2 | Logout then login (simulated golden) | session restored | behavior/reg-login.md | qa | 2026-11-08 |
| A3 | Open home anonymous then authed (simulated; after rework) | redirect then content | behavior/protected-home.md | qa | 2026-11-08 |
| A4 | Restart + login (simulated golden) | user still valid | FEATURE A4 note | qa | 2026-11-08 |

## Finding closed in rework

- F1 (high): anonymous home not redirected — fixed in implementation rework hop; re-verified pass.
