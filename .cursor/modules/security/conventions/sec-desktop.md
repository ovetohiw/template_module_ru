# sec-desktop

**Who reads:** security when `desktop` ∈ surfaces.

## Must

- Treat UI/renderer as untrusted; privileged ops outside UI process.
- IPC/messages from UI: validate schema/size; no ambient trust of sender payload.
- Secrets in OS-backed secure storage (keychain/credential store), not plaintext settings/files.
- Path and shell: user-influenced paths allowlisted; no shell string concat of user input.
- Require FEATURE must covering local data at rest if sensitive.

## Should

- Minimal privileged surface area documented in must[].

## Forbidden

- Electron-only flags as the only must; convention relay to eng.
