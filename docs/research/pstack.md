# pstack skills

Source: [Cursor plugins, `pstack`](https://github.com/cursor/plugins/tree/main/pstack), inspected from the repository's current `main` branch.

## What pstack is

pstack is a Cursor plugin built around `/poteto-mode`, a sticky routing skill that selects a playbook for a task and calls the other skills as needed. Its stated goal is to produce less code with stronger verification and to make parallel agent work safer.

`/setup-pstack` configures the models used for coding, judgment, and review roles. `/automate-me` can generate a personal mode skill from recent transcripts.

## Skills

### Main workflow and routing

- `poteto-mode`: Main entry point. Routes tasks through playbooks for investigation, bugs, performance, features, refactors, prototypes, visual parity, skill authoring, evaluation, PR work, shipping, autonomous runs, orchestration, and worktree cleanup.
- `figure-it-out`: Designs an auditable workflow for large or unusual work when no narrower playbook fits.
- `show-me-your-work`: Records decisions, evidence, and outcomes in a reviewable TSV log.
- `recall`: Reconstructs recent work context before starting or resuming a task.
- `setup-pstack`: Detects available models and writes the model-role configuration.

### Understanding and design

- `how`: Explains how a subsystem works, including runtime flow, ownership, placement, and layering.
- `why`: Investigates design rationale and tradeoffs against available project evidence.
- `teach`: Combines `how` and `why` into a plain explanation of a change or subsystem.
- `architect`: Settles types, signatures, and module structure before implementation.
- `arena`: Runs several competing solutions, then combines the strongest parts.
- `swarm`: Runs parallel workers over separate slices or exploration paths and returns one report.
- `interrogate`: Runs adversarial, multi-model review to find blind spots in a change.
- `blast-radius`: Finds what a small change could break outside its diff and proves safety with runtime evidence.

### Building and verification

- `tdd`: Runs TDD when the user explicitly asks for it or a cheap local regression test is obvious.
- `create-verification-skill`: Generates a project-local skill that drives the real app and proves user-visible behavior.
- `maintain-verification-skill`: Audits and updates an existing verification skill and its feature map.
- `no-comments`: Reviews comments with Comment Sicko, fixes accepted findings, and suggests structural alternatives.
- `typescript-best-practices`: Applies the plugin's TypeScript guidance.
- `make-bot-ui`: Builds a bot-driven page or dashboard around a webhook and Tailscale.

### Skill and writing work

- `automate-me`: Mines transcripts for personal working preferences and drafts or updates a user-specific mode skill.
- `reflect`: Reviews a completed session and proposes concrete improvements to existing skills.
- `technical-writing`: Reviews or writes docs, READMEs, RFCs, PR descriptions, and commit messages using a layered documentation standard.
- `unslop`: Removes common AI writing patterns.
- `bro`: Restates the previous message in plain language without jargon.

### Principles

pstack also contains 21 small, model-invoked principle skills. They cover deletion-first refactoring, foundational data modeling, first-principles redesign, minimizing reader load, outcome-focused migrations, user experience, design alternatives, building reusable tools, domain modeling, boundary discipline, type-system discipline, idempotent operations, deleting legacy APIs after caller migration, avoiding shared mutable state, proving behavior, fixing root causes, sequencing verifiable units, protecting context, not blocking on reversible human decisions, and encoding lessons in structure.

## Most relevant to this repo and its maintainer

1. `automate-me`: Closest match to the repo's goal of making an agent workflow personal. It could generate an `ask-zac`-style mode, although your repo currently prefers an explicit router over a broad sticky mode.
2. `poteto-mode`: A strong comparison point for `ask-zac`. It routes by playbook and keeps the detailed routing logic in one place, but it is more autonomous and implementation-oriented.
3. `reflect`: Directly relevant to improving this skills repo after real sessions. It proposes changes only after several reviewers identify a lesson worth encoding.
4. `technical-writing`: Useful for syncing skill docs, READMEs, and plugin-facing prose. It overlaps with `writing-for-agents`, but focuses more on the document type and reader experience.
5. `create-verification-skill` and `maintain-verification-skill`: Relevant if you want this repo to test skills through realistic harness behavior rather than only checking files and manifests.
6. `interrogate`, `arena`, and `swarm`: Relevant for evaluating skill changes, comparing prompt variants, and parallelizing repository audits.
7. `show-me-your-work` and `sequence-verifiable-units`: Relevant to long-running skill migrations and broad documentation changes.
8. `principle-encode-lessons-in-structure`: Especially relevant here. It argues for turning repeated guidance into metadata, scripts, or checks instead of adding more prose.
9. `principle-minimize-reader-load`, `principle-subtract-before-you-add`, and `principle-laziness-protocol`: Good lenses for reducing overlap between `ask-zac`, `grilling`, `writing-for-agents`, and the engineering workflow skills.
10. `setup-pstack`: Relevant only if you adopt pstack itself. It configures pstack's model roles, not this repository's plugin manifests.

## Important overlap and differences

- Your repo has explicit, user-invoked workflow skills such as `ask-zac`, `to-spec`, `to-tickets`, and `implement`. pstack centralizes more of that behavior behind one sticky `/poteto-mode` entry point.
- Your repo's `code-review`, `diagnosing-bugs`, `domain-modeling`, `prototype`, `research`, `tdd`, and `writing-for-agents` cover much of pstack's engineering and documentation territory.
- pstack is stronger on multi-model review, autonomous runs, live verification, worktree orchestration, and personal style capture.
- Your repo is stronger on explicit issue-tracker flows, triage, domain records, ADRs, tracker-backed specs, and handoffs between planning and implementation.
- pstack includes its own `unslop`, which overlaps with the always-applied writing rule already present in your environment.
