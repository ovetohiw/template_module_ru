# eng-io

**Кто читает:** engineering, когда package затрагивает files/paths/uploads.

## Must

- Validate size, type и encoding; отклоняй path traversal (`..`, absolute escapes).
- User-influenced paths остаются внутри allowlisted root.
- Temp files очищаются; secrets не пишутся в world-readable paths.

## Should

- Stream large files вместо unbounded memory buffers.

## Forbidden

- Shelling out с unsanitized user path/filename fragments.
