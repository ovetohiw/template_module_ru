# sec-web

**Кто читает:** security, когда `web` ∈ surfaces. Только угол review.

## Must

- Требуй server authz на каждое sensitive HTTP action; помечай IDOR risk (object id от client).
- Cookie sessions: httpOnly; Secure в prod; документируй SameSite decision.
- Отклоняй `Access-Control-Allow-Origin: *` с credentials.
- Errors не должны утекать stack traces, tokens или internal paths клиентам.
- State-changing browser flows нуждаются в CSRF defense или эквиваленте при cookie auth.

## Should

- Rate-limit auth endpoints укажи в must/should, когда brute-force релевантен.

## Forbidden

- Копирование текста eng-web/qa-web как canon этого файла; framework-specific dogma как must.
