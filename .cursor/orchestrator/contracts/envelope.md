# Envelope (модуль → оркестратор)

Обязательные поля:

```text
case_id:
from_layer:          # layer id, не папка модуля
task_type:           # analyst: spec|accept; иначе n/a или вид пакета
verdict:             # pass | fail | blocked | needs_input
summary:             # 1–3 предложения; не SoR
blockers: []
artifacts: []        # пути
payload:             # schema по слою
written_at:
```

## Запрещено в выводе модуля

- `to_role`, `to_module`, `next_module`
- проза, направляющая другой отдел («передай в разработку»)
- цитирование чужих process модулей как authority

Неполный envelope → orchestrator hard; lifecycle не продвигается.
