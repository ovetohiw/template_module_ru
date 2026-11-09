# FEATURE (активный кейс)

- ID: golden-web-001
- Title: Простой сайт с БД, авторизацией и UI
- Status: in_progress
- surfaces: [web]
- design_skip: true
- design_skip_reason: "golden protocol; no visual refs"
- design:
  refs_index: cases/current/refs/_index.md
  pack: cases/current/design/
  screens: []
- Goal: Пользователи могут зарегистрироваться/войти и видеть базовый authenticated UI на базе базы данных.
- Scope in:
  - Оболочка Web UI
  - Auth пользователя (register/login/logout)
  - Постоянное хранилище пользователей в БД
- Scope out:
  - Платежи, OAuth social login, admin CMS, multi-tenant
- Acceptance:
  - [x] A1: Посетитель может зарегистрироваться с email+password и попасть в authenticated state
  - [x] A2: Зарегистрированный пользователь может снова войти после окончания сессии
  - [x] A3: Authenticated UI показывает защищённый home view; анонимный пользователь перенаправляется на login
  - [x] A4: Записи пользователей сохраняются в настроенной базе данных после перезапуска
- Status note: золотое демо закрыто с симулированными продуктовыми evidence (протокол harness реальный)
- Behavior paths:
  - cases/current/behavior/reg-login.md
  - cases/current/behavior/protected-home.md
- Security must:   # заполняет security-модуль в case SoR (не через ретрансляцию conventions)
  - [x] M1: Пароли хранятся как сильные хеши; без plaintext в БД/репозитории
  - [x] M2: Session cookie httpOnly (или эквивалентное безопасное решение по хранению сессии зафиксировано)
  - [x] M3: AuthZ на сервере; скрытие в UI ≠ authorization
  - [x] M4: Нет secrets/tokens в репозитории, FEATURE или evidence-артефактах
- Security should:
  - [ ] S1: Короткий TTL сессии + явный logout инвалидирует сессию
- Notes: Золотой сценарий для harness v1 (не продуктовая реализация).
