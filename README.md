# Designing with AI

A method, an agent skill, and notes for directing AI design work so it does not land on generic slop.

Models pick the color, layout, and copy most likely to please everyone. That is why so many one-shot apps share a purple gradient, a left-aligned hero, and a glowing orb on the right. This repo is a process for getting past that default.

It synthesizes three public sources (September 2026):

| Source | What it contributes |
| --- | --- |
| [Jaimin](https://x.com/jaimintf/status/2097031826024038755) / Appllama | Same prompt, different context. Name **flows of App A** and **design of App B**. Study real screens before generating. |
| [Matt Dailey](https://x.com/reactiverobot/status/2092638003789439075) | Constraints first (Alexander). No wackamole. Remove. Design tool, not product. Components + `/showcase`. Preview deploys. Steal screenshots. Taste as reps. |
| [Anshu Chimala via Lenny](https://www.lennysnewsletter.com/p/how-to-turn-your-ai-into-a-world) | Discover / Define / Deliver. Seed strings. Ambitious briefs. Critic subagent on screenshots. Image and video generation. Cut. |

The skill tells an agent what to do. The notes are for you. Templates are copy-paste.

## Method in one page

1. **Do not start in the product.** Iterate in Figma, HTML, Cursor Design Mode, or a `/showcase` page. Prototype gravity is real. The first graft into the app becomes the only direction you ever refine.
2. **Write the constraints** before any solution. When feedback arrives, ask whether it changes a constraint. If not, log a papercut. If a constraint must change, restart.
3. **Steal named products, not vibes.** Attach screenshots. Prompt: *flows of [App A], design of [App B]*.
4. **Discover: force variety.** Models cannot act randomly. Use a seed string (`openssl rand -hex 32`) or a slightly dangerous brief. Generate 3–4 independent takes. Do not deepen the first one.
5. **Define: critic on pixels.** A fresh critic sees a screenshot, never the repo. Stronger model as critic, cheaper as implementer. Stop after 1–2 loops unless the score is rising.
6. **Deliver: remove.** Walk every element: do I need that? Prefer native controls. Evaluate with real data.
7. **Hand off.** Write `docs/design-constraints.md`, attach winning references, then implement.

Full write-up: [notes/method.md](notes/method.md).

## Agent skill

[`skills/design-with-ai/`](skills/design-with-ai/) works with Grok, Claude, and Cursor.

```bash
# Grok (user profile, all projects)
cp -R skills/design-with-ai ~/.grok/skills/

# Claude Code
cp -R skills/design-with-ai ~/.claude/skills/

# This repo only
mkdir -p .agents/skills
cp -R skills/design-with-ai .agents/skills/
```

Then run `/design-with-ai`, or ask to design a screen, de-slop a UI, or one-shot an app. The skill tells the agent to propose constraints and 3–4 directions and wait before building in the product.

Score screens that already exist with `design-audit` (Grok user skill). Load this skill when generating.

## Repo map

```
skills/design-with-ai/     Agent procedure
notes/                     Human notes, one per source plus the synthesis
templates/                 Constraints, critic, one-shot, seed string, papercuts
```

| File | Use |
| --- | --- |
| [notes/method.md](notes/method.md) | The combined process |
| [notes/jaimin.md](notes/jaimin.md) | Named-product one-shots and reference libraries |
| [notes/dailey.md](notes/dailey.md) | Constraints, removal, prototype gravity |
| [notes/chimala.md](notes/chimala.md) | Discover / Define / Deliver |
| [notes/sources.md](notes/sources.md) | Bibliography |
| [templates/constraints.md](templates/constraints.md) | Blank constraints note for a project |
| [templates/critic.md](templates/critic.md) | Pixel-only critic prompt |
| [templates/oneshot.md](templates/oneshot.md) | Flows-of / design-of prompt |
| [templates/seed-string.md](templates/seed-string.md) | Variety loop |
| [templates/papercuts.md](templates/papercuts.md) | Hold minor annoyances for a cohesive pass |

Lenny's Technique 7 (“remove AI tells”) is paywalled. Read it at the source. Appllama's own skills stay upstream: [Appllama/appllama-skills](https://github.com/Appllama/appllama-skills). MCP: `https://mcp.appllama.io/mcp`. This repo has no generated mock UIs.

## License

MIT. The notes quote and paraphrase public posts with attribution. Read the originals; they are better than the summaries.
