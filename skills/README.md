# Skills

| Skill | Job |
| --- | --- |
| [`design-with-ai`](design-with-ai/) | Constraints, named products, variants, critic, cut |
| [`appllama-usage`](appllama-usage/) | Appllama MCP research playbooks |
| [`appllama-app-design-skill`](appllama-app-design-skill/) | Expo / RN native build bar + simulator loop |

Appllama pair is vendored from [Appllama/appllama-skills](https://github.com/Appllama/appllama-skills). See [UPSTREAM.md](UPSTREAM.md).

Install user-wide:

```bash
npx skills@latest add appllama/appllama-skills -g -a grok -a claude-code -y --copy
cp -R design-with-ai ~/.grok/skills/
```

In this repo, Grok/Codex also load `.agents/skills/` (symlinks here).

Trigger: `/design-with-ai`, `/appllama-usage`, `/appllama-app-design-skill`.
