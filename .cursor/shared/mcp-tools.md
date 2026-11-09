# Карта MCP tools

Декларации проекта: [`.cursor/mcp.json`](../mcp.json). Персональный MCP остаётся в `~/.cursor/mcp.json` (никогда не коммить).

**Gate ≠ включённый server.** Строка ниже может *разрешать* инструмент при совпадении `surfaces[]`; server *включён* только если он есть в `mcp.json`. Пустой `mcpServers` + surface `web` → используй `stack.md` / ручные evidence.

Перезапусти Cursor после изменения `mcp.json`.

## Политика (дефолты шаблона)

| Module | Gate | Optional MCP | Purpose |
|--------|------|--------------|---------|
| qa | `web` ∈ CASE/FEATURE `surfaces[]` | Playwright (когда включён в mcp.json) | Browser verify / evidence |
| analyst | — | none in template | docs MCP = Phase B |
| engineering | — | none | runners → `stack.md` |
| security | — | none | conventions + code review |

## Правила

- MCP — **опциональный инструмент evidence**, не runner-slot и не замена `shared/stack.md`.
- Если MCP недоступен или не включён → `stack.md` / ручные evidence; **не invent success**.
- Не ретранслируй списки MCP tools через OUTBOX (не convention relay).
- Пини версии пакетов; никаких секретов в `mcp.json` (только `${env:NAME}`).
- MCP **не** security boundary.

## Включить позже (Phase B) — Playwright

Для реального web-продукта смержи в `.cursor/mcp.json` (pin, никогда `@latest`):

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

Тогда qa может использовать его только когда `web` ∈ `surfaces[]` и server реально доступен.
