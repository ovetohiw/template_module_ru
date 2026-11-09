# design verify

Pack DoD — `pass` / `pack_complete=true` только если всё выполняется:

- `refs/_index.md` валиден: у каждого screen_id есть существующий файл `primary_ref`
- `TOKENS.md`: colors bg, surface, text, text-muted, border, accent; type ≥ body+title+button; space scale; radius; без TBD на primary screens
- `SCREENS.md`: секция на каждый primary screen — zones, key sizes, alignment, states из index
- `COMPONENTS.md`: controls, нужные screens, или явно `none`
- `DECISIONS.md`: conflicts / fidelity limits (кратко ок)
- FEATURE.design.pack + screens заполнены

Иначе `needs_input` или `blocked`. Без brand invention сверх refs. Без product code.
