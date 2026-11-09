# Schema evidence

Каждый acceptance criterion / обязательный check нуждается в одной строке:

| Поле | Обязательно |
|------|-------------|
| criterion | текст или id |
| command_or_action | что было запущено/сделано |
| result | наблюдаемый outcome |
| artifact | путь или ссылка на лог |
| role | какой модуль автор строки |
| session | дата или id сессии |
| rework_target | на строках **fail**: `implementation` \| `design` \| `requirements` (опционально; по умолчанию implementation) |

## Невалидное доказательство

- "ok" / "passed" / "done" без command+result+artifact
- Только developer-строки там, где ownership у QA
- Пропуск обязательных checks без CASE waiver + human hard
