---
name: design-with-ai
description: >
  Direct AI design work so it is not generic slop. Use when the user asks to
  design with AI, de-slop a UI, one-shot an app or landing page, generate
  variants, run a design critic loop, or runs /design-with-ai. Covers
  constraints-first design, named product references, seed-string variety,
  critic subagents, and cutting until the screen holds.
---

# Design with AI

Load this when generating or directing UI, not when auditing an existing visual system. For a Jobs/Ive pass over screens that already exist, use `design-audit`.

Default: propose a constraint list and 3–4 directions, then wait for the user to pick one before building in the product.

## 0. Do not start in the product

Iterate in a design surface first: HTML prototype, Figma, Cursor Design Mode, or a `/showcase` page of components. Building the first take in the real app creates prototype gravity. Later prompts only patch that graft.

If the user already has a live screen, still extract constraints and references before editing pixels.

## 1. Write the constraints

List every constraint before any solution. Typical buckets: jobs to be done, required states, platform (HIG / M3), type and spacing rules, performance, what must not exist.

When feedback arrives, ask whether it **changes a constraint**. If it does not, log it as a papercut. Do not prompt “make X more prominent” as a one-off. That is wackamole design; it produces a disjoint patchwork.

If a constraint must be added or dropped, restart from this step. (Alexander: *Notes on the Synthesis of Form*.)

Keep a papercuts list. Ship obvious breaks immediately. Hold minor annoyances for a cohesive pass.

## 2. Steal named products, not vibes

Generic “make it beautiful” collapses to the same purple-gradient landing page. Name the **flow** and the **look** separately, then one-shot from that.

Pattern (from Appllama / Jaimin):

> Use [reference library or MCP if present]. Build [product]. It should have the **flows of [App A]** and the **design of [App B]**.

Collect screenshots of products that already solved the same problem. Attach them. Do not describe “clean and modern.”

If Appllama MCP is connected, study real top-grossing screens first. If not, still attach 4–8 screenshots before generating.

## 3. Discover: force variety

The model cannot act randomly. “Make it unique” still yields the same layout.

**Seed string (Sakana SSOT):**

1. Generate a long random alphanumeric string in the shell (`openssl rand -hex 32`).
2. Derive color, type, layout, and motif from subpatterns in that string.
3. Do not print the string in the UI.

Run this **3–4 times**. Present the variants. Do not deepen the first one.

**Ambitious brief:** the user names a specific, slightly dangerous inspiration (a game still, an interior, an industrial panel). Ask the model for a broad, shallow list of directions, then the user steers. AI-generated ideas pasted back into AI stay average.

## 4. Define: critic loop

Do not ask the implementer to “improve the design.” It will defend its own code.

Each iteration:

1. Screenshot the current UI (no code, no prior critique).
2. Fresh critic context: name the aesthetic, imagine a top studio executing it, list the biggest gaps, score /10.
3. Penalize overdone AI patterns (purple gradients, left-text/right-orb, glow, extra labels).
4. Implement only the critic’s gaps.
5. Stop after 1–2 loops unless the score is rising. Do not put the 9/10 stop rule in the critic prompt.

Prefer a stronger model as critic and a cheaper one as implementer. Critic sees **pixels**, never the repo.

When image or video tools exist, instruct the agent to use them. Code-only gradients and shapes are an AI tell. Do not put API keys in the product; local gitignored env only.

## 5. Deliver: remove

Agents add copy, lines, icons, and custom chrome. Walk every element: **do I need that?**

Prefer native controls over restyled ones. Prefer one grid of meaning over labels that repeat the image. Delete glow, extra containers, and explanatory prose.

Separate views from logic. New UI pieces land on a `/showcase` (or equivalent) before they touch product data.

Evaluate with **real data** (preview deploy, simulator, or fixture that matches production shape). Unit tests do not prove a frontend.

Taste is a solution library from reps. After each variant, name what you felt, not only what was wrong.

## 6. Hand-off

After a direction is chosen:

- Update or create a short constraints note in the repo (`docs/design-constraints.md` or the project’s existing design doc).
- Attach the winning reference screenshots.
- Only then implement in the product.

If the user asked only for directions, stop after presenting variants. Do not silently start coding.
