# eng-config

**Who reads:** engineering.

## Must

- No secrets in committed config; placeholders only.
- Prod secrets from env/secret store — never FEATURE/chat.
- Safe local defaults; fail fast on missing required settings.

## Should

- Explicit config over hidden globals.

## Forbidden

- Hardcoded production credentials.
