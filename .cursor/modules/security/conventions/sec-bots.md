# sec-bots

**Who reads:** security when `bots` ∈ surfaces. Channel-agnostic (Telegram/MAX/…).

## Must

- Bot tokens/secrets never in repo, logs, or FEATURE — env/secret store only.
- Inbound webhook/update: HTTPS; verify shared secret header before parse (e.g. Telegram `X-Telegram-Bot-Api-Secret-Token`); timing-safe compare.
- Callback/button payloads untrusted — server authz for the action/object.
- Idempotency for updates (dedupe update ids) before side effects.
- Rate-limit per user/chat for expensive actions.
- Fast ack to platform; heavy work async — avoid retry storms.

## Should

- Separate dev/prod bots; rotate on leak.

## Forbidden

- Telegram-only API names as sole must; trusting callback data for authz.
