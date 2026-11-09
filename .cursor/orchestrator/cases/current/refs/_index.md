# refs index (шаблон)

Сопоставить каждый экран с primary ref. Модуль design читает только этот файл (плюс перечисленные пути).

```text
# screen_id:
#   primary_ref: <относительный путь под refs/>
#   states: []          # опциональные доп. файлы (error, empty, …)
#   priority: primary   # primary | secondary
#   ignore: []          # watermarks, browser chrome, …
```

## Screens

(нет — человек заполняет до design hop, когда нужна визуальная fidelity)
