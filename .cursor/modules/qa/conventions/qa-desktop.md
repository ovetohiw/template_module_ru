# qa-desktop

**Who reads:** qa when `desktop` ∈ surfaces. Verify angle.

## Must

- Verify privileged actions cannot be triggered from UI without validated bridge/IPC path (per FEATURE).
- Confirm secrets are not readable from plain settings/files in the test environment.
- Path/upload cases: reject traversal / outside allowlist when in acceptance.

## Should

- Restart app and confirm session/secret behavior matches FEATURE.

## Forbidden

- Skipping IPC/local checks because “eng unit tests passed”.
