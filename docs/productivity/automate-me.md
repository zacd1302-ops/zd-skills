## What it does

`automate-me` turns repeated working preferences into a personal `-mode` skill. It mines workspace-scoped transcripts, checks patterns with you, drafts the skill, and runs the prose through `unslop`.

It requires repeated evidence before it turns a preference into a rule. A single unusual conversation is not enough.

## When to reach for it

You invoke this by typing `/automate-me`, and the agent won't reach for it on its own. Reach for it when you want agents to follow your established style, delegation habits, verification rules, or response preferences. For one narrow workflow, write a regular skill instead.

## The personal mode

The generated mode is user-invoked by default because it is heavy and opinionated. Run it again to update an existing mode from the history since its last edit. Review the draft before shipping it.

## It's working if

- The draft names repeated preferences with evidence from more than one session.
- It avoids copying other skills into the mode and points to them instead.
- The mode has a narrow trigger and changes how the agent works when explicitly invoked.

## Where it fits

`automate-me` is a reach-for-it-anytime productivity standalone. It pairs with [reflect](https://aihero.dev/skills-reflect) for lessons from one session and [writing-for-agents](https://aihero.dev/skills-writing-for-agents) for the resulting skill's structure. [ask-zac](https://aihero.dev/skills-ask-zac) routes across the full set.
