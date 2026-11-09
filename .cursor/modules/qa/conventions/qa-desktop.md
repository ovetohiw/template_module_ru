# qa-desktop

**Кто читает:** qa, когда `desktop` ∈ surfaces. Угол verify.

## Must

- Verify, что privileged actions нельзя вызвать из UI без validated bridge/IPC path (по FEATURE).
- Подтверди, что secrets не читаются из plain settings/files в test environment.
- Path/upload cases: отклоняй traversal / outside allowlist, когда это в acceptance.

## Should

- Перезапусти app и подтверди, что session/secret behavior соответствует FEATURE.

## Forbidden

- Пропускать IPC/local checks потому что «eng unit tests passed».
