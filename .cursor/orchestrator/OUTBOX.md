# OUTBOX

# Бриф оркестратора → один модуль. v1: только один pending OUTBOX.

- status: empty
  # empty | pending | done
- assigned_module:
  # analyst | design | security | engineering | qa
- layer:
  # requirements | design | security | implementation | verification | acceptance
- task_type:
  # analyst: spec | accept; иначе вид пакета / n/a
- package_id:
  # id work_package (в execution)
- case_id: golden-web-001
- brief: |
  # текстовый бриф задачи
- artifacts_in: []
  # входные пути артефактов
- written_at:
  # время записи

# Для design-брифа дополнительно (см. ROUTING):
# feature_path, refs_index, surfaces, pack_dir, rework
