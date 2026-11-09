# eng-config

**Кто читает:** engineering.

## Must

- Без secrets в committed config; только placeholders.
- Prod secrets из env/secret store — никогда из FEATURE/chat.
- Безопасные local defaults; fail fast при отсутствии required settings.

## Should

- Явный config вместо скрытых globals.

## Forbidden

- Hardcoded production credentials.
