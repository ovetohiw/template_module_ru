# qa-web

**Кто читает:** qa, когда `web` ∈ surfaces. Угол verify.

## Must

- Проверяй authz на sensitive actions (не только UI visibility).
- Пытайся horizontal access к resource ids другого пользователя, когда применимо.
- Подтверди, что errors не раскрывают stacks/tokens; cookie flags, если cookie auth в FEATURE.
- Подтверди, что anonymous vs authenticated routes соответствуют acceptance.
- Когда CASE `design_status=done`: visual evidence vs каждый primary_ref + tokens checklist из design pack; fail rows включают `rework_target`.

## Should

- Spot-check CSRF/session logout behavior, когда это в acceptance.
- Используй Playwright MCP для behavioral evidence, когда он mapped в `shared/mcp-tools.md` **и** server доступен в project `mcp.json`; иначе stack/manual screenshots.

## rework_target (fail)

- visual mismatch при valid pack → `implementation`
- pack противоречит refs / token gaps → `design`
- behavior acceptance неверен → `requirements`

## Forbidden

- Считать «button hidden» proof authz; переписывать design pack; копировать eng-web как verify canon.
