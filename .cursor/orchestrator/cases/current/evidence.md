# Evidence

Строки по [.cursor/shared/evidence-schema.md](../../../shared/evidence-schema.md).

| criterion | command_or_action | result | artifact | role | session |
|-----------|-------------------|--------|----------|------|---------|
| A1 | Ручной/скриптовый register flow (симулированный golden) | новый пользователь authenticated | behavior/reg-login.md | qa | 2026-11-08 |
| A2 | Logout затем login (симулированный golden) | сессия восстановлена | behavior/reg-login.md | qa | 2026-11-08 |
| A3 | Открыть home анонимно, затем authed (симулировано; после rework) | redirect, затем контент | behavior/protected-home.md | qa | 2026-11-08 |
| A4 | Restart + login (симулированный golden) | пользователь всё ещё валиден | FEATURE A4 note | qa | 2026-11-08 |

## Finding, закрытый в rework

- F1 (high): анонимный home не перенаправлялся — исправлено в implementation rework hop; повторная проверка pass.
