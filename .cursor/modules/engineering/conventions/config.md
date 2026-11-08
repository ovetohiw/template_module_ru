# config (engineering)

**Who reads:** engineering only. **Who does not:** other modules.

## Must

- No secrets in committed config; placeholders only.
- Document new non-secret knobs in code/comments or project config registry if the repo has one.
- Defaults safe for local/dev; prod secrets from environment/secret store — never FEATURE/chat.

## Should

- Prefer explicit config over hidden globals.
- Fail fast on missing required non-default settings.

## Forbidden

- Hardcoded production credentials.
- Copying security convention files into the app tree.
