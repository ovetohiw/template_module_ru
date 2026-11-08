# Evidence schema

Every acceptance criterion / required check needs one row:

| Field | Required |
|-------|----------|
| criterion | text or id |
| command_or_action | what was run/done |
| result | observed outcome |
| artifact | path or log ref |
| role | which module authored the row |
| session | date or session id |

## Invalid proof

- "ok" / "passed" / "done" without command+result+artifact
- Developer-only rows where QA ownership is required
- Skipped mandatory checks without CASE waiver + human hard
