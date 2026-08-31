## What it does

`blast-radius` finds what a change could break outside its diff and proves the central safety fact by running the real code. It looks past callers that a text search can find, including wire formats, runtime timing, downstream readers, and library behavior.

A convincing explanation is not proof. The skill marks safety facts as unproven when it cannot reach a runnable check.

## When to reach for it

You invoke this by typing `/blast-radius`, and the agent won't reach for it on its own. Reach for it when a small-looking change feels risky or before merging a change with hidden consumers. Use [code-review](https://aihero.dev/skills-code-review) for a broader standards and spec review.

## Find the one safety fact

The useful result is usually one fact that makes most risks disappear. The skill traces that fact through source and dependencies, then tries to reach the strongest cheap evidence, from a source line to a real test or running app.

## It's working if

- The report names the changed behavior and the central safety fact.
- Confirmed risks include a location, likelihood, cost, and check.
- The report shows the command or test that proved the safety fact, or says it remains unproven.

## Where it fits

`blast-radius` is a reach-for-it-anytime engineering standalone. It complements [how](https://aihero.dev/skills-how) for runtime behavior and [why](https://aihero.dev/skills-why) for design rationale. [ask-zac](https://aihero.dev/skills-ask-zac) routes across the full set.
