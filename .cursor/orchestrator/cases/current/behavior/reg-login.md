# Сценарий: регистрация и вход

## Happy path

1. Открыть форму register; отправить валидные email+password.
2. Система создаёт пользователя; сессия authenticated.
3. Logout; login с теми же credentials успешен.

## Failures

- Дубликат email → видимая ошибка; без сессии.
- Неверные credentials → видимая ошибка; без сессии.
