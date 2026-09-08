# Discover, Define, Deliver

Source: [Anshu Chimala, “How to turn your AI into a world-class designer,” Lenny’s Newsletter, 2026-09-01](https://www.lennysnewsletter.com/p/how-to-turn-your-ai-into-a-world). Public techniques 1–6 are summarized here. Technique 7 is paywalled and is not restated.

Chimala’s diagnosis: models are trained to make the safe next token. Great design starts from feeling and makes unexpected choices. If you can push the model off the mode, you get at the rest of the distribution. The Double Diamond, rewritten for agents:

1. **Discover** — go broad. Variety and ambitious briefs.
2. **Define** — give one direction a personality. Critic loops, generated imagery.
3. **Deliver** — cut until it holds.

## Discover

### Seed strings

Asking for “something unique” still produces the same purple-gradient, left-text, right-graphic landing page. Asking the model to “decide at random” produces tokens that *sound* random (the same pottery metaphor, the same palette) because the model cannot sample uniformly. Randomness has to come from outside.

Sakana AI’s String Seed of Thought: generate a long alphanumeric string in the shell, derive the creative direction from subpatterns in that string, do not print the string in the UI. Each run is actually different.

Template: [templates/seed-string.md](../templates/seed-string.md).

### Ambitious briefs

Be specific and slightly wild. A pixel-art game still, an isometric city of features, a radically asymmetric layout. The hard part is inventing the ask.

A system that keeps the originality on your side of the table:

1. Ask the model for a *broad, shallow* list of directions. No detail. The list is kindling.
2. You react. Name what you felt. Steer (“tactile, not cartoony; texture, not gray gradients”).
3. Iterate until the direction is yours, then ask the model to write the build prompt.

Pasting AI ideas straight back into AI is how everyone else would have done it. Prompts that fail are worth saving and retrying on newer models.

## Define

### Critic subagent

The implementer is not objective. It sees its own code and the effort already spent.

Each iteration: screenshot → fresh critic with *only* the screenshot → aesthetic, studio-level execution, biggest gaps, score /10 → implement the gaps.

Setup that matters:

- Criteria as objective as you can make them. Worst: “judge if it looks beautiful.” Better: “imagine a top studio executing this aesthetic, score against that.” Best: rank 4 professional examples + 1 current screenshot by polish.
- Example images as a moodboard, not a target. Do not ask it to copy.
- Stop after 1–2 loops unless scores rise. A 9/10 stop rule in the critic prompt either never fires or rubber-stamps.
- Stronger model as critic, cheaper as implementer. The critic can be a small fraction of tokens.

Template: [templates/critic.md](../templates/critic.md).

### Image (and video) generation

Coding agents prefer gradients, shapes, and CSS patterns. Those are AI tells. Tell the agent to use image tools. Keys stay in a gitignored env file and do not ship.

Video models are not only for ads. Two uses from the public piece: looping clips with the background matted out, layered into UI; and interpolating between keyframe stills so a scroll or gesture scrubs a transition.

## Deliver

### Cut what does not add value

AI adds. Premium reads as restraint. On a “clean, minimalist” calorie tracker the first take still had glow, random text highlights, labels that repeated the food photos, and custom controls that lost to native iOS.

The push: simplify to an image-centric grid, delete gradients / glow / extra containers, use native components, tighten type. The model will not take that risk on its own — deleting code is risky in its training.

Walk the screen. Ask what needs to be there. Less on screen can hold attention better than more.

### Technique 7

Paywalled at the source. Not restated in this repo.
