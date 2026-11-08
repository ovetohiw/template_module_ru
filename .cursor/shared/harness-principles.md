# Harness principles (constitution)

Immutable without human hard approval. Keep this file ≤1 screen.

1. **Hub-and-spoke** — modules never address each other; no `to_role` / `to_module`.
2. **Thin root** — root `AGENTS.md` is router only; no role how-to.
3. **Process under `.cursor/`** — never place process files in product tree.
4. **Lifecycle gates** — forbidden edges in `LIFECYCLE.md` stay closed.
5. **Raw brief isolation** — user intake never becomes qa/engineering OUTBOX.
6. **Evidence before done** — no summary-only close; no role self-close.
7. **One role per session** — autonomy C only inside engineering stages.
8. **SoR matrix** — status only in CASE / INBOX / OUTBOX / handoffs.log / role PROGRESS.
9. **Load isolation** — no foreign `modules/*/processes` or `conventions`; conventions are **role-prefixed** (`eng-*`/`qa-*`/`sec-*`/`analyst-*`), never travel via OUTBOX; load **core** always, **domain** by package trigger, **surface** only if id ∈ CASE/FEATURE `surfaces[]` (web|desktop|bots); `shared/stack.md`, `shared/mcp-tools.md`, `invariants`, `evidence-schema` are allowed shared reads (not convention relay).
10. **Contracts before prose** — new layer/hop needs schema under `orchestrator/contracts/`.
11. **Skills thin** — skills are entrypoints; they do not duplicate full DoD.
12. **No always-load-all** — alwaysApply must not load every module.
13. **MCP tools** — declarations in project `.cursor/mcp.json`; secrets only via `${env:NAME}`; MCP is not a security boundary; pin versions; least privilege; policy in `shared/mcp-tools.md` only.
