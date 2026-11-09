# eng-tooling

**Кто читает:** engineering.

## Must

- Install/build/test только из `shared/stack.md` или OUTBOX hints.
- Пустые слоты stack → отметь в PROGRESS; без изобретённого CI.
- Чини красный listed baseline перед наложением новой работы, когда baseline есть.

## Should

- Предпочитай repo scripts, уже прописанные в stack.md.

## Forbidden

- Использование qa conventions для tooling; fake pass без запуска listed command.
