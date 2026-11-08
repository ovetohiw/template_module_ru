# uidesign (analyst)

**Who reads:** analyst only (when UI in scope). **Who does not:** engineering/qa — they follow FEATURE acceptance, not this file.

## Must

- UI acceptance is observable (what user sees/does), not CSS class names.
- First-viewport / primary flows stated if UI is in scope.
- Auth/gated UI: anonymous vs authenticated outcomes in behavior + acceptance.
- If refs exist later, FEATURE points to them; do not invent a brand system in Spec.

## Should

- One short UI contract block in FEATURE; details in behavior files.
- Note a11y-critical flows (focus/error text) when they are acceptance-relevant.

## Forbidden

- Telling engineering which framework/components to use (unless already in stack.md).
- Shipping this file path to other modules via OUTBOX.
- Hiding-button-as-security as an acceptance substitute for real authz (authz belongs in FEATURE security section after security hop).
