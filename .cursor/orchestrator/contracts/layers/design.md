# Layer payload: design

```text
design_paths: []           # пути записанных файлов pack
screens: []                # покрытые screen_ids
open_questions: []
pack_complete: true|false  # DoD из design verify
rework: false|true         # эхо OUTBOX.rework
```

Pack DoD (`pack_complete=true` только если всё выполнено): см. module design verify / LIFECYCLE.

Артефакты живут под FEATURE.design.pack (по умолчанию `cases/current/design/`).
Refs index: FEATURE.design.refs_index (по умолчанию `cases/current/refs/_index.md`).
