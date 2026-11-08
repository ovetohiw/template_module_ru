# qa-bots

**Who reads:** qa when `bots` ∈ surfaces. Verify angle.

## Must

- Reject requests without valid inbound secret (or document blocked environment).
- Replay/duplicate update does not double side effect (idempotency).
- Unauthorized callback/user cannot perform privileged action.
- No bot token appears in logs/evidence captured for the run.

## Should

- Abuse: rapid repeated commands rate-limited when in FEATURE.

## Forbidden

- Trusting platform delivery alone without secret check when webhook mode is in scope.
