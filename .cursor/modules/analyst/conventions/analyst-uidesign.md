# analyst-uidesign

**Who reads:** analyst (GUI). **Who does not:** eng/qa (they use FEATURE); design owns visual extraction.

## Must

- UI acceptance = what user sees/does, not CSS/framework names.
- Auth UI: anonymous vs authenticated outcomes in acceptance/behavior.
- Primary flows stated when GUI in scope.
- Stub FEATURE.design paths (`refs_index`, `pack`) when web|desktop in surfaces.
- Apply design_skip policy (see spec process): forbidden skip when brief demands mockup match or refs present; allowed skip needs `design_skip_reason`.
- If visual fidelity required and `refs/_index.md` missing → `needs_input` (human lays out refs) — do not set skip to bypass.

## Should

- Note a11y-critical error/focus text when acceptance-relevant.
- List expected screen ids under FEATURE notes when known.

## Forbidden

- Visual extraction (tokens/spacing/screen blueprints) — that is the **design** module.
- Dictating UI framework unless in stack.md; shipping this file via OUTBOX; UI-hide as authz substitute.
