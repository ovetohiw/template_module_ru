# Schema work_package

Payload analyst `spec` должен включать `work_packages[]`:

```text
id:                      # уникальная строка
layer:                   # только allowlist (ниже)
goal:                    # один ясный outcome
depends_on: []           # ids других пакетов
acceptance: []           # наблюдаемые проверки
artifacts_expected: []   # пути или виды артефактов
constraints: []          # опционально
```

## Правила

- allowlist `layer`: **`security` | `implementation` | `verification` only**
- `design`, `requirements`, `acceptance` — stage/envelope hops — **никогда** не `work_package.layer`
- нет путей `.cursor/modules/...`
- deps должны существовать и быть ацикличны
- `verification` должен зависеть от `implementation` (по умолчанию)
- когда CASE `design_status=done`: каждый пакет `implementation` должен перечислить путь design pack в `artifacts_expected` или `constraints`
