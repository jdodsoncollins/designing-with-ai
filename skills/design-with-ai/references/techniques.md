# Techniques

Load this when running Discover / Define loops. Do not paste into every turn.

## Seed string

```bash
openssl rand -hex 32
```

Then: derive palette, type, layout, and motif from the string; keep the string out of the UI; produce 3–4 independent takes.

Source: Sakana AI String Seed of Thought, used in Anshu Chimala / Lenny’s Newsletter (2026-09-01).

## Critic prompt (pixels only)

Give the critic a screenshot and nothing else:

- Name the aesthetic this screen is attempting.
- Describe how a top studio would execute that aesthetic.
- List the biggest gaps (structure first, then detail).
- Flag overdone / obviously AI-generated patterns.
- Score /10 against the studio bar, not against the last iteration.

Do not tell the critic the stop score. The implementer stops after 1–2 loops unless scores rise.

Better critic: rank 4 professional examples + 1 current screenshot by polish.

## Named-product one-shot

```
Use [library/MCP if available]. Build [name].
Flows of [App A]. Design of [App B].
```

Example (Jaimin / Appllama, 2026-09-07): Stelari. Flows of Chani, design of Blank Spaces.

## Cut list

Walk the screen and delete, in order:

1. Glow, gradients, and decorative containers
2. Labels that repeat what an image or control already says
3. Custom buttons/fields that lose to platform chrome
4. Extra icons and hairlines
5. Copy that explains the UI instead of doing the job
