## What it does

`technical-writing` reviews or writes technical documents through four checks: document type, reader-directed sentences, single-thought sentences, and unambiguous wording. It covers tutorials, how-to guides, reference pages, explanations, READMEs, RFCs, PR descriptions, and commit messages.

The goal is prose a tired engineer understands on the first read. The codebase's real paths, symbols, and commands take priority over invented descriptions.

## When to reach for it

You invoke this by typing `/technical-writing`, and the agent won't reach for it on its own. Reach for it when writing or reviewing technical documentation. For agent instructions such as skills and `AGENTS.md`, use [writing-for-agents](https://aihero.dev/skills-writing-for-agents) as the primary guide.

## Pick the document mode

Choose tutorial, how-to, reference, or explanation before editing. Keep instructions as commands, put conditions before guarded steps, and split sentences that carry more than one thought. Apply [unslop](https://aihero.dev/skills-unslop) to remove AI writing tells.

## It's working if

- The document has one clear job and one matching Diátaxis mode.
- Instructions say who does what and use real project names.
- A reader can follow each sentence without guessing what a pronoun or condition refers to.

## Where it fits

`technical-writing` is a reach-for-it-anytime productivity standalone. It complements [writing-for-agents](https://aihero.dev/skills-writing-for-agents) for agent-facing documents and [unslop](https://aihero.dev/skills-unslop) for prose cleanup. [ask-zac](https://aihero.dev/skills-ask-zac) routes across the full set.
