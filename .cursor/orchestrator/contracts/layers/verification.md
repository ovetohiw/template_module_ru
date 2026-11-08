# Layer payload: verification

```text
package_id:
pass_fail_by_criterion: []   # criterion → pass|fail
findings: []                 # id, severity, summary, artifact, rework_target?
evidence_rows: []            # evidence-schema.md
```

## findings[].rework_target

On fail rows / findings, set:

```text
rework_target: implementation | design | requirements
```

Rules:

- visual mismatch with valid design pack → `implementation`
- pack contradicts refs / token gaps → `design`
- behavior acceptance wrong → `requirements`
- field missing → orchestrator defaults to `implementation`
