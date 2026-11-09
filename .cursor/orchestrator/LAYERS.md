# Layers (абстрактные слоты)

| Layer id | Назначение | Привязанный модуль (см. ROUTING) | work_package? |
|----------|------------|----------------------------------|---------------|
| requirements | Нормализовать бриф; FEATURE; work_packages | analyst (`spec`) | no (stage hop) |
| design | Visual SoR из refs → design pack | design | no (stage hop) |
| security | Threat/constraints must/should | security | yes |
| implementation | Сборка по пакетам | engineering | yes |
| verification | Независимые evidence / findings | qa | yes |
| acceptance | Гейт закрытия vs FEATURE + evidence | analyst (`accept`) | no (stage hop) |

Модули планируют по **layer ids**, никогда по именам папок модулей.

`design` — это **lifecycle stage + envelope layer**, не `work_package.layer`. См. таблицу stage-vs-package в LIFECYCLE.
