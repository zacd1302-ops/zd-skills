## What it does

`arena` runs several independent attempts at the same task, compares them against a concrete rubric, and combines the strongest result into one artifact. Each candidate writes separately, so unfinished work cannot overwrite another candidate.

The skill does not treat parallel output as finished work. It reads every candidate, records the choice and rejected ideas, then verifies the combined result.

## When to reach for it

You invoke this by typing `/arena`, and the agent won't reach for it on its own. Reach for it when several designs could work and choosing one before seeing alternatives would be risky. For separate work slices, use [swarm](https://aihero.dev/skills-swarm).

## The arena loop

The loop has six phases: frame the artifact and rubric, fan out candidates, cross-judge them, pick a base, graft useful ideas, and verify the result. The rubric must be specific enough to grade, such as "preserves the public API" or "adds a failing regression test".

## It's working if

- Each candidate received the same task and wrote to its own location.
- The final artifact has a named base, recorded grafts, and rejected ideas.
- Verification tests the synthesized artifact, not just the candidates' explanations.

## Common questions

**When should I use this instead of one strong agent?**

Use it when the shape of the answer is uncertain. Do not pay for several attempts when the task is mechanical or already constrained by an agreed design.

## Where it fits

`arena` is a reach-for-it-anytime engineering standalone. It pairs with [prototype](https://aihero.dev/skills-prototype) for design questions and [interrogate](https://aihero.dev/skills-interrogate) for adversarial review. [ask-zac](https://aihero.dev/skills-ask-zac) routes across the full set.
