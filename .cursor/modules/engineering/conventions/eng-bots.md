# eng-bots

**Кто читает:** engineering, когда `bots` ∈ surfaces. Угол build (Telegram/MAX/…).

## Must

- Загружай bot tokens из env/secret store; никогда не коммить и не логируй их (вкл. URL paths).
- Verify inbound webhook secret до parsing body; timing-safe compare.
- Deduplicate update ids до side effects; делай handlers idempotent.
- Authorize callback actions на server (callback payload ≠ proof of rights).
- Acknowledge platform быстро; тяжёлую работу обрабатывай async.
- Per-user rate limits на costly operations.

## Should

- Подписывайся только на update types, которые обрабатываешь.

## Forbidden

- Доверять unsigned inbound без secret; Telegram-only musts, которые ломают другие каналы.
