# Envelope (module → orchestrator)

Required fields:

```text
case_id:
from_layer:          # layer id, not module folder
task_type:           # analyst: spec|accept; else n/a or package kind
verdict:             # pass | fail | blocked | needs_input
summary:             # 1–3 sentences; not SoR
blockers: []
artifacts: []        # paths
payload:             # per-layer schema
written_at:
```

## Forbidden in module output

- `to_role`, `to_module`, `next_module`
- prose directing another department (“передай в разработку”)
- foreign module process citations as authority

Incomplete envelope → orchestrator hard; lifecycle does not advance.
