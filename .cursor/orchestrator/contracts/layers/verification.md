# Layer payload: verification

```text
package_id:
pass_fail_by_criterion: []   # criterion → pass|fail
findings: []                 # id, severity, summary, artifact, rework_target?
evidence_rows: []            # evidence-schema.md
```

## findings[].rework_target

На fail-строках / findings задай:

```text
rework_target: implementation | design | requirements
```

Правила:

- визуальное расхождение при валидном design pack → `implementation`
- pack противоречит refs / пробелы в токенах → `design`
- неверные behavior acceptance → `requirements`
- поле отсутствует → оркестратор по умолчанию ставит `implementation`
