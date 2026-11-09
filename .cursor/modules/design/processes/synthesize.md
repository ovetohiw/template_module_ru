# Process: synthesize

1. Прочитай [../conventions/INDEX.md](../conventions/INDEX.md): design-refs + surface files по `surfaces[]`.
2. Читай только OUTBOX: `feature_path`, `refs_index`, `pack_dir`, `surfaces`, `rework`.
3. Если `refs_index` отсутствует или невалиден → `needs_input` (человек должен предоставить refs/_index). Не изобретай brand.
4. Прочитай primary refs из `_index.md` (image Read). Извлеки eng-facing pack в `pack_dir`:
   - TOKENS.md
   - SCREENS.md
   - COMPONENTS.md
   - DECISIONS.md
5. Обнови FEATURE.design: pack path, refs_index, screens[].
6. Выполни DoD из [../verify.md](../verify.md).
7. INBOX envelope `from_layer=design` + [design payload](../../../orchestrator/contracts/layers/design.md); stop.

## Do not

- Product code; правка plan.md / work_packages; чужие conventions; scrape chat-image вне путей refs_index; relay conventions через OUTBOX.
