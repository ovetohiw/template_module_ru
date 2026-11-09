# sec-desktop

**Кто читает:** security, когда `desktop` ∈ surfaces.

## Must

- Считай UI/renderer untrusted; privileged ops вне UI process.
- IPC/messages от UI: validate schema/size; без ambient trust sender payload.
- Secrets в OS-backed secure storage (keychain/credential store), не plaintext settings/files.
- Path и shell: user-influenced paths allowlisted; без shell string concat user input.
- Требуй FEATURE must про local data at rest, если sensitive.

## Should

- Minimal privileged surface area задокументирован в must[].

## Forbidden

- Electron-only flags как единственный must; relay conventions в eng.
