# design-web

**Кто читает:** design, когда `web` ∈ surfaces.

## Must

- Укажи target viewport(s) на каждый screen (например desktop width; mobile, если есть ref).
- Отмечай scroll vs fixed regions, когда это видно в ref.
- Form / nav / content zones явно в SCREENS.md.

## Should

- Выноси responsive unknowns в open_questions, когда есть ref только для одного breakpoint.

## Forbidden

- Изобретать breakpoints или components, не подразумеваемые refs; копировать eng-web/qa-web как этот файл.
