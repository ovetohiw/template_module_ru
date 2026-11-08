# eng-ui

**Who reads:** engineering **only when** CASE `design_status=done`. Build angle vs design pack.

## Must

- Implement UI strictly against FEATURE.design.pack (TOKENS / SCREENS / COMPONENTS).
- No style invention outside the pack (colors, type, radii, spacing, layout zones).
- Honor DECISIONS.md fidelity limits; open gaps → blocker / ask via INBOX, do not freestyle brand.

## Should

- Prefer CSS variables / tokens mirroring TOKENS.md role names.

## Forbidden

- Interpreting PNG refs as sole SoR when pack exists; reading design module conventions; copying qa-web as this file.
- Loading this file when `design_status` is `skipped` or `not_applicable`.
