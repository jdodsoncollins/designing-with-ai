# Named-product one-shots

Source: [Jaimin, 2026-09-07](https://x.com/jaimintf/status/2097031826024038755) and the follow-up with MCP / skills / prompt.

## The claim

Two one-shots, same prompt, same model (Astra). The left app looks like every AI astrology app. The right one does not. The difference is not the prompt. It is the skill stack: Appllama MCP + skills vs none.

Jaimin: “if your app looks like the left one, it’s a skill problem.”

## The prompt

Follow-up, same thread:

> Use appllama mcp & skills, build an astrology app Stelari, it should have the flows of Chani and design it like Blank Spaces.

That sentence does three things the usual “make a beautiful astrology app” prompt does not:

1. **A reference library** — real top-grossing screens, not the model’s memory of “nice UI.”
2. **Flows of a named product** — information architecture and motion of Chani, not “onboarding then home.”
3. **Design of a named product** — visual system of Blank Spaces, not “clean and modern.”

Flow and look are different products on purpose. Copying both from one app is how you get a clone. Crossing them is how you get a specific new thing.

## What to steal from this

- Attach screenshots. Every designer Dailey has worked with starts a project that way. The MCP is a shortcut for the same move.
- Name two products, not one adjective.
- One-shot from that. Do not “explore the vibe” for six turns and then generate.
- If Appllama (or any screen catalog) is connected, study first, generate second. MCP: `https://mcp.appllama.io/mcp`. Skills: [Appllama/appllama-skills](https://github.com/Appllama/appllama-skills).

## What not to do

Do not re-describe Blank Spaces in prose (“soft serif, cream, generous margin”). The model will average that description with a thousand other cream-serif landing pages. Name the product and attach frames.

Template: [templates/oneshot.md](../templates/oneshot.md).
