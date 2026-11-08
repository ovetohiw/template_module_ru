# Process: synthesize

1. Read [../conventions/INDEX.md](../conventions/INDEX.md): design-refs + surface files per `surfaces[]`.
2. Read OUTBOX only: `feature_path`, `refs_index`, `pack_dir`, `surfaces`, `rework`.
3. If `refs_index` missing or invalid → `needs_input` (human must provide refs/_index). Do not invent brand.
4. Read primary refs listed in `_index.md` (image Read). Extract eng-facing pack into `pack_dir`:
   - TOKENS.md
   - SCREENS.md
   - COMPONENTS.md
   - DECISIONS.md
5. Update FEATURE.design: pack path, refs_index, screens[].
6. Run [../verify.md](../verify.md) DoD.
7. INBOX envelope `from_layer=design` + [design payload](../../../orchestrator/contracts/layers/design.md); stop.

## Do not

- Product code; edit plan.md / work_packages; foreign conventions; chat-image scrape outside refs_index paths; OUTBOX convention relay.
