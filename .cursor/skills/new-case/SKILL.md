---
name: new-case
description: >-
  Открывает новый кейс оркестратора из брифа пользователя. Для /new-case,
  «новая задача», «хочу фичу» или NL product-запроса, когда активного кейса нет.
---

# new-case

1. Если CASE уже активен (stage не idle/closed) → hard; сначала закрой или continue.
2. Установи CASE: новый `case_id`, stage `analysis`, `surfaces: []` (analyst заполнит), сохрани `raw_brief`, status in progress.
3. Запиши OUTBOX: `assigned_module=analyst`, `layer=requirements`, `task_type=spec`, status pending.
4. Обнови orchestrator PROGRESS next_step → запустить role-analyst.
5. **Стоп.** Не запускай analyst в этом ходе.
