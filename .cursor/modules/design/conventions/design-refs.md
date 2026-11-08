# design-refs

**Who reads:** design. **Who does not:** eng/qa/analyst (they consume FEATURE.design + pack).

## Must

- SoR inputs = `refs_index` paths only; no chat-image scrape.
- Each screen in `_index.md` has one `primary_ref`; conflicts → DECISIONS.md; do not average silently.
- Emit eng-facing pack: TOKENS, SCREENS, COMPONENTS, DECISIONS — sizes, colors, type, space, layout zones, states.
- Pass only if [../verify.md](../verify.md) DoD holds.
- Write FEATURE.design.pack / screens; open_questions for gaps — no brand invention beyond refs.
- `needs_input` if index/refs missing when design hop required.

## Should

- Note fidelity limits (crop, watermark ignore) in DECISIONS.md / index `ignore`.

## Forbidden

- Product code; editing plan.md; shipping this file via OUTBOX; reading foreign conventions; weakening DoD to force green.
