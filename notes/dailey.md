# Constraints, removal, prototype gravity

Source: [Matt Dailey, “How I Design with AI,” 2026-08-26](https://x.com/reactiverobot/status/2092638003789439075). Engineer, not a designer, hates slop. Written while building Ref.

The seven points, compressed for use. Read the original; the voice is the point.

## 1. Always consider the whole

Three steps, from Christopher Alexander, *Notes on the Synthesis of Form*:

1. Lay out all the constraints you are designing for.
2. Consider an array of solutions that satisfy those constraints.
3. If a constraint must be added or one can be removed, go to 1.

Constraints can be type, sizing, workflows, or business-logic states. You decide them.

The common failure is skipping step 3 and playing **wackamole**. A user is confused; you prompt “make X more prominent” or “add an affordance to do Y.” AI is extremely good at that prompt and extremely bad at the whole. You get a disjoint patchwork that randomly prioritizes some interactions over others.

When feedback arrives, ask whether it changes a constraint before jumping to a solution. Keep a papercuts list: move fast on obvious breaks, track minor annoyances, address them cohesively when you next redesign.

## 2. Remove stuff

Agents love to add — in code (extra try/catch, reimplemented utilities) and in UI (copy, lines, icons). The result often looks better than what an engineer would draw by hand and is still kind of bad.

Look at every element. Ask: do I actually need that?

## 3. Iterate in a design tool

Do not iterate on design in the product. Use a tool with fine control and low extra context: Figma, Cursor Design Mode, Claude Design, HTML prototypes.

**Prototype gravity** is the silent killer. The agent builds v1 in the real codebase. Refining that graft feels cheaper than exploring. Designing in the real app also forces a version that must attach to existing routes, data, and chrome — so you never see the other shapes.

Generate 3–4 variants of everything.

## 4. Use components and libraries

Separate views from logic. Reusable components. Visual cohesion instead of a patchwork of reimplemented buttons.

At Ref they keep a `/showcase` page. Agents build the UI piece there and play with it before it touches the main app.

## 5. Use preview deploys

The best evaluation is real data. Even if the agent built exactly what you asked, holding it against production data will show you it is wrong.

Frontend needs a human and a preview URL. Backend can be verified with tests. Split those PRs when a feature spans both.

## 6. Steal stuff

Most UX problems are already solved. Start every project by pulling screenshots of products that solved a similar problem or communicated a similar idea. That packet is the best context you can give an agent.

## 7. Explore your taste

Taste is reflecting on your own reaction to something. Engineers are excellent at identifying that a design does not work and short on a solution library. Building the library is reps: try, feel, name the feeling, try again.

At Ref they thresh: throw a design in the middle and beat it with sticks until it holds.

## How this sits with the others

Dailey is the spine of the skill: constraints, papercuts, don’t start in the product, `/showcase`, preview deploys, steal screenshots, cut. Jaimin is how you steal with precision (named flow + named look). Chimala is how you get variety and a critic that isn’t the implementer.
