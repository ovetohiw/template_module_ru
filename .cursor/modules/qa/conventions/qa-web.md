# qa-web

**Who reads:** qa when `web` ∈ surfaces. Verify angle.

## Must

- Check authz on sensitive actions (not only UI visibility).
- Attempt horizontal access to another user’s resource ids when applicable.
- Confirm errors do not expose stacks/tokens; cookie flags if cookie auth in FEATURE.
- Confirm anonymous vs authenticated routes match acceptance.

## Should

- Spot-check CSRF/session logout behavior when in acceptance.

## Forbidden

- Treating “button hidden” as authz proof; copying eng-web as verify canon.
