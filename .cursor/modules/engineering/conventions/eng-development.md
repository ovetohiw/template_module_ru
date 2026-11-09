# eng-development

**Кто читает:** engineering. **Кто не читает:** другие модули.

## Must

- Scope одного package/FEATURE; без drive-by refactors.
- Tech только из `shared/stack.md` (hard, если выбор отсутствует).
- Diff только то, что нужно package.
- Соблюдай FEATURE Security must[] как текст кейса (не sec-* files).
- Возвращай только INBOX — без feature-level «done».

## Should

- Следуй существующим паттернам репо; exec-plans для крупной работы; autonomy C = только следующий stage.

## Forbidden

- Изобретение runners; secrets в commits; запуск qa/security/accept здесь; чужие conventions.
