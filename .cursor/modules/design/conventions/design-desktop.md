# design-desktop

**Кто читает:** design, когда `desktop` ∈ surfaces.

## Must

- Отмечай window chrome vs app content, если оба есть в refs; предпочитай app content как layout SoR, если index не говорит иное.
- Density / spacing из primary_ref; документируй platform widget look-alikes только если они явно в ref.

## Should

- Помечай OS-native controls vs custom chrome в DECISIONS.md.

## Forbidden

- Предполагать Electron/Tauri/etc., если этого нет в stack.md / FEATURE; копировать eng-desktop как этот файл.
