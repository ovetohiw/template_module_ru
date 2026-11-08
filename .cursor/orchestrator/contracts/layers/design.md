# Layer payload: design

```text
design_paths: []           # pack file paths written
screens: []                # screen_ids covered
open_questions: []
pack_complete: true|false  # DoD from design verify
rework: false|true         # echoes OUTBOX.rework
```

Pack DoD (pack_complete=true only if all hold): see module design verify / LIFECYCLE.

Artifacts live under FEATURE.design.pack (default `cases/current/design/`).
Refs index: FEATURE.design.refs_index (default `cases/current/refs/_index.md`).
