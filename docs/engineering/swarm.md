## What it does

`swarm` sends independent workers across separate slices of a task, or races them against the same brief, then returns one compact report. Workers get separate writable locations when they produce files.

The parent defines the done predicate before starting and reports missing workers, gaps, and evidence instead of hiding them in a combined summary.

## When to reach for it

You invoke this by typing `/swarm`, and the agent won't reach for it on its own. Reach for it when the work divides cleanly into independent checks, explorations, or races. For several competing implementations of one artifact, use [arena](https://aihero.dev/skills-arena).

## Shape the work first

Choose slices, a race, or a mix before spawning workers. For races, declare whether the first passing result wins, all results are ranked, or the best result is selected. Every brief states its scope, verification command, and report format.

## It's working if

- Every required slice has a `PASS`, `ISSUES`, or `BLOCKED` result with evidence.
- Workers did not write to the same path.
- The final report names gaps, dropouts, and the selection rule when a race ran.

## Where it fits

`swarm` is a reach-for-it-anytime engineering standalone. It pairs with [show-me-your-work](https://aihero.dev/skills-show-me-your-work) for long runs and [blast-radius](https://aihero.dev/skills-blast-radius) when the parallel work checks change risk. [ask-zac](https://aihero.dev/skills-ask-zac) routes across the full set.
