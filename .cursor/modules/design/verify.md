# design verify

Pack DoD — `pass` / `pack_complete=true` only if all hold:

- `refs/_index.md` valid: each screen_id has existing `primary_ref` file
- `TOKENS.md`: colors bg, surface, text, text-muted, border, accent; type ≥ body+title+button; space scale; radius; no TBD on primary screens
- `SCREENS.md`: section per primary screen — zones, key sizes, alignment, states from index
- `COMPONENTS.md`: controls needed by screens, or explicit `none`
- `DECISIONS.md`: conflicts / fidelity limits (short ok)
- FEATURE.design.pack + screens filled

Else `needs_input` or `blocked`. No brand invention beyond refs. No product code.
