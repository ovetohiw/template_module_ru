# eng-io

**Who reads:** engineering when package touches files/paths/uploads.

## Must

- Validate size, type, and encoding; reject path traversal (`..`, absolute escapes).
- User-influenced paths stay inside an allowlisted root.
- Temp files cleaned up; no secrets written to world-readable paths.

## Should

- Stream large files instead of unbounded memory buffers.

## Forbidden

- Shelling out with unsanitized user path/filename fragments.
