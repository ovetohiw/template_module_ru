# qa-web

**Who reads:** qa when `web` ∈ surfaces. Verify angle.

## Must

- Check authz on sensitive actions (not only UI visibility).
- Attempt horizontal access to another user’s resource ids when applicable.
- Confirm errors do not expose stacks/tokens; cookie flags if cookie auth in FEATURE.
- Confirm anonymous vs authenticated routes match acceptance.
- When CASE `design_status=done`: visual evidence vs each primary_ref + tokens checklist from design pack; fail rows include `rework_target`.

## Should

- Spot-check CSRF/session logout behavior when in acceptance.
- Use Playwright MCP for behavioral evidence when mapped in `shared/mcp-tools.md` **and** the server is available in project `mcp.json`; otherwise stack/manual screenshots.

## rework_target (fail)

- visual mismatch with valid pack → `implementation`
- pack contradicts refs / token gaps → `design`
- behavior acceptance wrong → `requirements`

## Forbidden

- Treating “button hidden” as authz proof; rewriting design pack; copying eng-web as verify canon.
