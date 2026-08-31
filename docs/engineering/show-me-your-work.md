## What it does

`show-me-your-work` keeps one append-only TSV decision log for long-running or unattended work. Each row records what changed, why, the evidence, and the result.

The log is a review aid, not a transcript dump. Keep it local by default and commit it only when a reviewer needs the decision trail to trust the result.

## When to reach for it

You invoke this by typing `/show-me-your-work`, and the agent won't reach for it on its own. Reach for it before autonomous, multi-phase, or after-the-fact review work. For a short task, a normal summary is enough.

## The decision trail

Use `decisions.tsv` for one effort or `.audit/<task-slug>.tsv` when several efforts share a directory. Log forks, checkpoints, pivots, reverts, blockers, and verified units. Evidence must be a path, commit, issue, trace, or other pointer that a reviewer can follow.

## It's working if

- Each row fits on one line and names one decision or checkpoint.
- Evidence resolves to something that supports the row.
- The final audit matches the transcript and includes an independent reviewer's attention points.

## Where it fits

`show-me-your-work` is a reach-for-it-anytime engineering standalone. It pairs with [swarm](https://aihero.dev/skills-swarm) and [implement](https://aihero.dev/skills-implement) when work spans agents or phases. [ask-zac](https://aihero.dev/skills-ask-zac) routes across the full set.
