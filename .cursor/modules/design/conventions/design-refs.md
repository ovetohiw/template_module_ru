# design-refs

**Кто читает:** design. **Кто не читает:** eng/qa/analyst (они потребляют FEATURE.design + pack).

## Must

- SoR inputs = только пути `refs_index`; без scrape chat-image.
- У каждого screen в `_index.md` один `primary_ref`; conflicts → DECISIONS.md; не усредняй молча.
- Выдай eng-facing pack: TOKENS, SCREENS, COMPONENTS, DECISIONS — sizes, colors, type, space, layout zones, states.
- Pass только если выполняется DoD из [../verify.md](../verify.md).
- Запиши FEATURE.design.pack / screens; open_questions по gaps — без brand invention сверх refs.
- `needs_input`, если index/refs отсутствуют, когда design hop обязателен.

## Should

- Отмечай fidelity limits (crop, watermark ignore) в DECISIONS.md / index `ignore`.

## Forbidden

- Product code; правка plan.md; передача этого файла через OUTBOX; чтение чужих conventions; ослабление DoD ради зелёного статуса.
