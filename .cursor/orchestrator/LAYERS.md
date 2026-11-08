# Layers (abstract slots)

| Layer id | Purpose | Bound module (see ROUTING) | work_package? |
|----------|---------|----------------------------|---------------|
| requirements | Normalize brief; FEATURE; work_packages | analyst (`spec`) | no (stage hop) |
| design | Visual SoR from refs → design pack | design | no (stage hop) |
| security | Threat/constraints must/should | security | yes |
| implementation | Build against packages | engineering | yes |
| verification | Independent evidence / findings | qa | yes |
| acceptance | Gate close vs FEATURE + evidence | analyst (`accept`) | no (stage hop) |

Modules plan against **layer ids**, never against module folder names.

`design` is a **lifecycle stage + envelope layer**, not a `work_package.layer`. See LIFECYCLE stage-vs-package table.
