# eng-ui

**Кто читает:** engineering **только когда** CASE `design_status=done`. Угол build vs design pack.

## Must

- Реализуй UI строго по FEATURE.design.pack (TOKENS / SCREENS / COMPONENTS).
- Без style invention вне pack (colors, type, radii, spacing, layout zones).
- Соблюдай fidelity limits из DECISIONS.md; открытые gaps → blocker / ask через INBOX, не freestyle brand.

## Should

- Предпочитай CSS variables / tokens, зеркалящие role names из TOKENS.md.

## Forbidden

- Интерпретировать PNG refs как единственный SoR, когда pack существует; читать conventions модуля design; копировать qa-web как этот файл.
- Загружать этот файл, когда `design_status` равен `skipped` или `not_applicable`.
