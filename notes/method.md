# The method

AI is a next-token predictor. At every design decision it fills in the tokens most likely to please everyone. The process below is how to force it off that average without pretending the model has taste of its own.

One loop. Dailey supplies the spine (constraints, whole, remove). Jaimin supplies the one-shot (named products, real screens). Chimala supplies the exploration and critic machinery (seed strings, ambitious briefs, pixel-only critic, generated imagery).

## 0. Surface, not product

Iterate in a design tool. Figma, an HTML prototype, Cursor Design Mode, Claude Design, or a `/showcase` route of components all count. The product codebase does not.

Prototype gravity is the cost of grafting v1 into the real app. Later prompts only patch that graft, so you never see the other three directions you should have compared.

Dailey: generate 3–4 variants of everything, in a tool meant for design.

## 1. Constraints before solutions

Alexander, via Dailey:

1. Lay out every constraint.
2. Consider an array of solutions that satisfy them.
3. If a constraint must be added or dropped, go to 1.

Constraints are jobs, states, platform rules, type, spacing, performance, and what must not exist. You decide them. The model does not.

The failure mode is wackamole: a user is confused, so you prompt “make X more prominent.” AI loves that prompt. You get a disjoint patchwork that randomly prioritizes some interactions over others.

When feedback arrives, ask: does this change a constraint? If yes, restart. If no, log a papercut. Ship obvious breaks now. Hold minor annoyances for a cohesive pass. Keep that list in the repo, [templates/papercuts.md](../templates/papercuts.md).

Blank sheet: [templates/constraints.md](../templates/constraints.md).

## 2. Named products, not adjectives

“Make it beautiful / clean / modern / unique” is how you get the purple landing page. The model has seen that sentence a million times.

Jaimin’s one-shot for Stelari, same prompt both times, one of them with Appllama MCP + skills:

> Use appllama mcp & skills, build an astrology app Stelari, it should have the flows of Chani and design it like Blank Spaces.

Split **flow** from **look**. Attach 4–8 screenshots of products that already solved the problem. If a reference library or MCP is connected, study real screens first. Do not describe the vibe; name the product.

Template: [templates/oneshot.md](../templates/oneshot.md).

## 3. Discover: variety from outside the model

The model cannot act randomly. Asking it to “make every decision at random” still yields the same palette, the same pottery metaphor, the same left-text / right-graphic split. Tokens that *sound* random are not random.

**Seed string (Sakana SSOT, via Chimala):** generate a long alphanumeric string in the shell, derive color / type / layout / motif from subpatterns, keep the string out of the UI, run it 3–4 times, present the variants, do not deepen the first one. Template: [templates/seed-string.md](../templates/seed-string.md).

**Ambitious brief:** you name a slightly dangerous inspiration (a game still, an isometric city, an industrial panel, a rule-breaking asymmetric layout). Ask the model for a *broad, shallow* list of directions. You react. You steer. Then you ask it to write the build prompt. AI-generated ideas pasted straight back into AI stay average; the steering is the original part. Save prompts that fail and retry them when models improve.

## 4. Define: a critic that never sees the repo

Asking the implementer to “improve the design” fails. It reviews its own code, its own rationale, and the effort already spent.

Each loop:

1. Screenshot the current UI.
2. Fresh critic context: screenshot only. No code, no prior critique, no implementation notes.
3. Name the aesthetic. Imagine a top studio executing it. List the biggest gaps (structure, then detail). Penalize overdone AI patterns. Score /10 against the studio bar, not the last iteration.
4. Implement only those gaps.
5. Stop after 1–2 loops unless the score is rising. Do not put the 9/10 stop rule in the critic prompt. It will never fire, or it will rubber-stamp.

Stronger (and more expensive) model as critic. Cheaper model as implementer. A good critic can be a small fraction of tokens and still change the identity of the screen.

A tighter critic: rank 4 professional examples + 1 current screenshot by polish. Concrete, visual, hard to waffle.

When image or video tools exist, tell the agent to use them. Code-only gradients, shapes, and patterns are an AI tell. Keys live in a gitignored env file and must not ship.

Template: [templates/critic.md](../templates/critic.md).

## 5. Deliver: remove

Agents add. Copy, lines, icons, glow, custom buttons, labels that repeat the image. Your job is the cut.

Walk every element: do I need that? Prefer native platform controls. Prefer one grid of meaning. Delete decorative containers and explanatory prose.

Separate views from logic. New pieces land on `/showcase` before they touch product data. Evaluate with real data (preview deploy, simulator, or a fixture that matches production shape). Unit tests do not prove a frontend. Backend can be verified in tests; frontend needs a human holding it.

Taste is a solution library built from reps: try, feel, name the feeling, try again. Engineers are good at spotting that a design does not work and short on examples of how to fix it. The threshing is the work.

## 6. Hand-off into the product

Only after a direction is chosen:

- Write or update `docs/design-constraints.md`.
- Attach the winning reference screenshots.
- Implement in the real app.

If the request was only for directions, stop. Do not silently start coding.

Score existing screens with `design-audit`. Appllama’s catalog stays upstream; use it in step 2 if it is installed. Lenny’s Technique 7 is paywalled; read it there.
