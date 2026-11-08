# Layers (abstract slots)

| Layer id | Purpose | Bound module (see ROUTING) |
|----------|---------|----------------------------|
| requirements | Normalize brief; FEATURE; work_packages | analyst (`spec`) |
| security | Threat/constraints must/should | security |
| implementation | Build against packages | engineering |
| verification | Independent evidence / findings | qa |
| acceptance | Gate close vs FEATURE + evidence | analyst (`accept`) |

Modules plan against **layer ids**, never against module folder names.
