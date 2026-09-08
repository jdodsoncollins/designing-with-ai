# Skills

`design-with-ai` is the only skill in this repo. It is the agent-facing procedure; human notes live in `/notes`.

Install:

```bash
cp -R design-with-ai ~/.grok/skills/          # Grok, all projects
cp -R design-with-ai ~/.claude/skills/        # Claude Code
mkdir -p ../.agents/skills && cp -R design-with-ai ../.agents/skills/
```

Trigger: `/design-with-ai`, or any request to design, de-slop, one-shot, generate variants, or run a design critic.

Do not also load a Jobs/Ive audit skill in the same turn unless the user asked to score existing screens.
