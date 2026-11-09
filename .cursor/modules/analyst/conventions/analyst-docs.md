# analyst-docs

**Кто читает:** analyst. **Кто не читает:** другие модули.

## Must

- Сценарии в `cases/current/behavior/`; FEATURE держит короткий contract + Behavior paths.
- Включай `surfaces: []` (web|desktop|bots) в FEATURE; синхронизируй с CASE.
- Оставляй Security must/should stubs для заполнения на security hop.
- При web|desktop: stub FEATURE.design (+ design_skip / reason по политике uidesign); не синтезируй visual pack.
- Только observable acceptance; hard к человеку, если behavior неизвестен.
- Accept: синхронизируй behavior или `unchanged` + reason.

## Should

- Один scenario file на каждый user-visible path.

## Forbidden

- Product code; secrets/PII в docs; process/DoD внутри behavior files; чужие conventions.
