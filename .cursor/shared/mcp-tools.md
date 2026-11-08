# MCP tools map

Project declarations: [`.cursor/mcp.json`](../mcp.json). Personal MCP stays in `~/.cursor/mcp.json` (never commit).

**Gate ≠ enabled server.** A row below may *allow* a tool when `surfaces[]` matches; the server is *on* only if it appears in `mcp.json`. Empty `mcpServers` + `web` surface → use `stack.md` / manual evidence.

Restart Cursor after changing `mcp.json`.

## Policy (template defaults)

| Module | Gate | Optional MCP | Purpose |
|--------|------|--------------|---------|
| qa | `web` ∈ CASE/FEATURE `surfaces[]` | Playwright (when enabled in mcp.json) | Browser verify / evidence |
| analyst | — | none in template | docs MCP = Phase B |
| engineering | — | none | runners → `stack.md` |
| security | — | none | conventions + code review |

## Rules

- MCP is an **optional evidence tool**, not a runner-slot and not a replacement for `shared/stack.md`.
- If MCP is unavailable or not enabled → `stack.md` / manual evidence; **do not invent success**.
- Do not relay MCP tool lists via OUTBOX (not a convention relay).
- Pin package versions; no secrets in `mcp.json` (use `${env:NAME}` only).
- MCP is **not** a security boundary.

## Enable later (Phase B) — Playwright

For a real web product, merge into `.cursor/mcp.json` (pin, never `@latest`):

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["-y", "@playwright/mcp@0.0.84"]
    }
  }
}
```

Then qa may use it only when `web` ∈ `surfaces[]` and the server is actually available.
