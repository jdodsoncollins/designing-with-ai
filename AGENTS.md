# Agents

This repo is a method and skill pack for directing AI design work. It is not an application.

## Load these skills

| Task | Skill |
| --- | --- |
| New UI, variants, de-slop, one-shot | `design-with-ai` |
| Study top-grossing apps (Appllama MCP connected) | `appllama-usage` |
| Build Expo / React Native screens | `appllama-app-design-skill` |
| Score screens that already exist | `design-audit` (user profile; not in this repo) |

For a new mobile screen: `design-with-ai` first (constraints, named products, 3–4 directions, then wait). If Appllama MCP is connected, run `appllama-usage` (`get_credits` is free) before drawing. Implement with `appllama-app-design-skill`. End in the simulator, not in code review.

Do not start in a product codebase. Do not harvest the Appllama catalog.

## MCP

```
https://mcp.appllama.io/mcp
```

Project copy: `.mcp.json`. Grok user config: `grok mcp add --transport http appllama https://mcp.appllama.io/mcp`. MCP access is Appllama Pro. Credits reset on the 1st UTC.

## Layout

Skills live in `skills/`. `.agents/skills/` is the auto-discovery path (symlinks). Notes and templates are for humans.

Appllama skills are vendored MIT copies of [Appllama/appllama-skills](https://github.com/Appllama/appllama-skills). Update from upstream; do not fork their playbooks here.
