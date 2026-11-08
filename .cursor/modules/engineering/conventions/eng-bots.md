# eng-bots

**Who reads:** engineering when `bots` ∈ surfaces. Build angle (Telegram/MAX/…).

## Must

- Load bot tokens from env/secret store; never commit or log them (incl. URL paths).
- Verify inbound webhook secret before parsing body; timing-safe compare.
- Deduplicate update ids before side effects; make handlers idempotent.
- Authorize callback actions on server (callback payload ≠ proof of rights).
- Acknowledge platform quickly; process heavy work async.
- Per-user rate limits on costly operations.

## Should

- Subscribe only to update types you handle.

## Forbidden

- Trusting unsigned inbound without secret; Telegram-only musts that break other channels.
