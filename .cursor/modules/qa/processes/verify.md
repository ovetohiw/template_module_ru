# Process: verify

1. Read [../conventions/INDEX.md](../conventions/INDEX.md): qa-test + surface files per `surfaces[]`.
2. Confirm verification package (not raw intake).
3. Exercise FEATURE acceptance (+ Security must where testable); if `design_status=done`, visual checks vs design pack / primary_ref.
4. Fail → findings[] with `rework_target` (`implementation`|`design`|`requirements`); verdict fail.
5. INBOX; stop. Do not assign engineering. No foreign conventions.
