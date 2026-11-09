# Сценарий: protected home

## Happy path

1. Authenticated пользователь открывает `/` (или home) → виден контент protected home.

## Failures

- Анонимный пользователь открывает home → redirect на login; без protected-контента.
