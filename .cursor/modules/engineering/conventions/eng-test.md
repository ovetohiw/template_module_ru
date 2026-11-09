# eng-test

**Кто читает:** engineering (пишет tests на build). **Кто не читает:** qa (см. qa-test).

## Must

- Новое/изменённое behavior: добавь или обнови automated checks до claim, что package ready.
- Bugfix: regression, который падает до фикса и проходит после.
- Предпочитай observable behavior, а не asserts порядка приватных вызовов.
- Mock boundaries (time, network, FS, third parties) — не unit under test.
- Запускай affected tests командами только из `shared/stack.md` или OUTBOX; пустые слоты → явно зафиксируй, не изобретай runners.
- Без реальных secrets/PII в fixtures.

## Should

- Именуй tests по behavior + expected outcome; arrange–act–assert.
- Трассируй к behavior scenario ids, когда они есть.

## Forbidden

- Fake green; молчаливый skip обязательных tests; копирование qa-test как этот canon; claim независимого qa verify.
