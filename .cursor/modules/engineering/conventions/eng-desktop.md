# eng-desktop

**Кто читает:** engineering, когда `desktop` ∈ surfaces. Угол build (platform-neutral).

## Must

- Держи privileged FS/network/credential work вне untrusted UI layer.
- Validate каждый IPC/message от UI (schema, size, semantics).
- Храни secrets через OS secure storage APIs — не plaintext config.
- Allowlist paths; без user-controlled shell interpolation.

## Should

- Минимизируй privileged API surface, открытый UI.

## Forbidden

- Node/OS full access из untrusted UI; Electron flag laundry lists как единственный must.
