## What it does

`reflect` mines a completed conversation for lessons that should change future agent behavior. Three reviewers examine judgment, tooling, and alternative interpretations, then a synthesizer routes findings to accepted edits, rejected ideas, or backlog.

It does not edit skills automatically. You approve the accepted changes before they land.

## When to reach for it

You invoke this by typing `/reflect`, and the agent won't reach for it on its own. Reach for it after a complex task, a correction, a dead end with a reusable fix, or a workflow that exposed a missing skill rule. Skip trivial sessions.

## Keep lessons durable

A lesson earns a skill edit only when it would change a future decision. If a script, lint rule, metadata flag, or runtime check would enforce it better than prose, route it there instead.

## It's working if

- Reviewers cite concrete moments from the active transcript.
- Accepted findings name a target skill and a specific behavior change.
- You see an approval gate before any skill edit is applied.

## Where it fits

`reflect` is a reach-for-it-anytime productivity standalone. It pairs with [automate-me](https://aihero.dev/skills-automate-me) for personal workflow rules and [writing-for-agents](https://aihero.dev/skills-writing-for-agents) for editing agent-facing documents. [ask-zac](https://aihero.dev/skills-ask-zac) routes across the full set.
