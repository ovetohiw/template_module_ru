# eng-desktop

**Who reads:** engineering when `desktop` ∈ surfaces. Build angle (platform-neutral).

## Must

- Keep privileged FS/network/credential work out of the untrusted UI layer.
- Validate every IPC/message from UI (schema, size, semantics).
- Store secrets via OS secure storage APIs — not plaintext config.
- Allowlist paths; no user-controlled shell interpolation.

## Should

- Minimize privileged API surface exposed to UI.

## Forbidden

- Node/OS full access from untrusted UI; Electron flag laundry lists as only must.
