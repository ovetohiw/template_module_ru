# sec-bots

**Кто читает:** security, когда `bots` ∈ surfaces. Channel-agnostic (Telegram/MAX/…).

## Must

- Bot tokens/secrets никогда в repo, logs или FEATURE — только env/secret store.
- Inbound webhook/update: HTTPS; verify shared secret header до parse (напр. Telegram `X-Telegram-Bot-Api-Secret-Token`); timing-safe compare.
- Callback/button payloads untrusted — server authz для action/object.
- Idempotency для updates (dedupe update ids) до side effects.
- Rate-limit per user/chat для expensive actions.
- Fast ack к platform; heavy work async — избегай retry storms.

## Should

- Разделяй dev/prod bots; rotate при leak.

## Forbidden

- Telegram-only API names как единственный must; доверять callback data для authz.
