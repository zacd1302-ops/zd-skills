# Agent skills

A collection of reusable skills for Claude Code, Codex, and other coding agents. The repository contains 47 skills:

- 35 promoted skills in the plugin
- 8 beta skills in `skills/in-progress/`
- 4 utility skills in `skills/misc/`

The original engineering skills come from [Matt Pocock](https://github.com/mattpocock). The pstack additions come from [Lauren Tan, known as poteto](https://github.com/poteto). This repository maintains and adapts both sets, and includes the custom `study-course` workflow.

## Start here

Use [`ask-zac`](./skills/engineering/ask-zac/SKILL.md) when you are unsure which skill or flow fits.

For most engineering work:

1. Run [`setup-matt-pocock-skills`](./skills/engineering/setup-matt-pocock-skills/SKILL.md) once per repository.
2. Run [`grill-with-docs`](./skills/engineering/grill-with-docs/SKILL.md) to settle the problem, terminology, and decisions.
3. Run [`to-spec`](./skills/engineering/to-spec/SKILL.md) for work that needs a durable spec.
4. Run [`to-tickets`](./skills/engineering/to-tickets/SKILL.md) to split the spec into dependency-aware tickets.
5. Run [`implement`](./skills/engineering/implement/SKILL.md) to build the tickets with TDD and code review.

Skip the spec and ticket steps for a small change. Run [`tdd`](./skills/engineering/tdd/SKILL.md) directly when you want a test-first implementation.

## Common tasks

| Task | Skill |
| --- | --- |
| Choose a workflow | [`ask-zac`](./skills/engineering/ask-zac/SKILL.md) |
| Clarify an idea in a repository | [`grill-with-docs`](./skills/engineering/grill-with-docs/SKILL.md) |
| Plan a large effort across sessions | [`wayfinder`](./skills/engineering/wayfinder/SKILL.md) |
| Triage incoming bugs or requests | [`triage`](./skills/engineering/triage/SKILL.md) |
| Understand project terminology | [`domain-modeling`](./skills/engineering/domain-modeling/SKILL.md) |
| Understand module shape | [`codebase-design`](./skills/engineering/codebase-design/SKILL.md) |
| Diagnose a hard bug | [`diagnosing-bugs`](./skills/engineering/diagnosing-bugs/SKILL.md) |
| Check risks beyond a diff | [`blast-radius`](./skills/engineering/blast-radius/SKILL.md) |
| Compare competing implementations | [`arena`](./skills/engineering/arena/SKILL.md) |
| Parallelize independent work | [`swarm`](./skills/engineering/swarm/SKILL.md) |
| Review a branch or PR | [`code-review`](./skills/engineering/code-review/SKILL.md) |
| Record decisions during long work | [`show-me-your-work`](./skills/engineering/show-me-your-work/SKILL.md) |
| Explain a subsystem or change | [`teach`](./skills/teaching/teach/SKILL.md) |
| Work through one week of supplied course material | [`study-course`](./skills/teaching/study-course/SKILL.md) |
| Write agent-facing documents | [`writing-for-agents`](./skills/productivity/writing-for-agents/SKILL.md) |
| Write technical documentation | [`technical-writing`](./skills/productivity/technical-writing/SKILL.md) |
| Remove AI writing tells | [`unslop`](./skills/productivity/unslop/SKILL.md) |

## Promoted skills

Promoted skills are included in the plugin. User-invoked skills run only when you type their name. Model-invoked skills can also run automatically when the task matches their description.

### Engineering

#### User-invoked

- [`ask-zac`](./skills/engineering/ask-zac/SKILL.md): Routes you to the right skill or workflow.
- [`grill-with-docs`](./skills/engineering/grill-with-docs/SKILL.md): Builds shared terminology and records decisions while grilling.
- [`triage`](./skills/engineering/triage/SKILL.md): Moves incoming issues through triage roles.
- [`improve-codebase-architecture`](./skills/engineering/improve-codebase-architecture/SKILL.md): Finds codebase deepening opportunities and grills through the selected one.
- [`setup-matt-pocock-skills`](./skills/engineering/setup-matt-pocock-skills/SKILL.md): Configures the tracker, labels, and domain document layout.
- [`to-spec`](./skills/engineering/to-spec/SKILL.md): Publishes a conversation as a tracker-backed spec.
- [`to-tickets`](./skills/engineering/to-tickets/SKILL.md): Splits a plan into tracer-bullet tickets with blocking edges.
- [`implement`](./skills/engineering/implement/SKILL.md): Builds tickets with TDD and closes with code review.
- [`wayfinder`](./skills/engineering/wayfinder/SKILL.md): Maps large efforts as decision tickets.
- [`arena`](./skills/engineering/arena/SKILL.md): Compares parallel attempts at one task and synthesizes the strongest result.
- [`swarm`](./skills/engineering/swarm/SKILL.md): Runs parallel workers over independent slices or races.
- [`show-me-your-work`](./skills/engineering/show-me-your-work/SKILL.md): Records a TSV decision trail for long-running work.
- [`blast-radius`](./skills/engineering/blast-radius/SKILL.md): Finds risks beyond a diff and proves the central safety fact.

#### Model-invoked

- [`prototype`](./skills/engineering/prototype/SKILL.md): Answers a design question with throwaway code.
- [`copse`](./skills/engineering/copse/SKILL.md): Uses Copse records and worktree links as the local issue tracker.
- [`diagnosing-bugs`](./skills/engineering/diagnosing-bugs/SKILL.md): Reproduces, instruments, fixes, and regression-tests hard bugs.
- [`research`](./skills/engineering/research/SKILL.md): Researches primary sources and writes cited Markdown.
- [`tdd`](./skills/engineering/tdd/SKILL.md): Runs a red-green-refactor loop one vertical slice at a time.
- [`domain-modeling`](./skills/engineering/domain-modeling/SKILL.md): Challenges terminology and records domain decisions.
- [`codebase-design`](./skills/engineering/codebase-design/SKILL.md): Designs deep modules with small interfaces and clean seams.
- [`code-review`](./skills/engineering/code-review/SKILL.md): Reviews changes against repository standards and the originating spec.
- [`resolving-merge-conflicts`](./skills/engineering/resolving-merge-conflicts/SKILL.md): Resolves merge or rebase conflicts by tracing intent.
- [`version-control`](./skills/engineering/version-control/SKILL.md): Always-on git discipline for engineering work: one worktree and branch per feature or fix, main stays clean, history stays readable, merges stay safe.
- [`wizard`](./skills/engineering/wizard/SKILL.md): Generates scripts for setup steps that require human action.

### Productivity

#### User-invoked

- [`grill-me`](./skills/productivity/grill-me/SKILL.md): Interviews you about a plan without writing repository state.
- [`handoff`](./skills/productivity/handoff/SKILL.md): Writes a compact handoff for another session or agent.
- [`to-questionnaire`](./skills/productivity/to-questionnaire/SKILL.md): Creates questions for someone else to answer.
- [`wait-what`](./skills/productivity/wait-what/SKILL.md): Re-explains a message that did not land.
- [`automate-me`](./skills/productivity/automate-me/SKILL.md): Creates or updates a personal mode skill from repeated preferences.
- [`reflect`](./skills/productivity/reflect/SKILL.md): Turns durable session lessons into approved skill edits.
- [`technical-writing`](./skills/productivity/technical-writing/SKILL.md): Writes and reviews technical documentation.

#### Model-invoked

- [`grilling`](./skills/productivity/grilling/SKILL.md): Provides the reusable interview method behind several workflows.
- [`writing-for-agents`](./skills/productivity/writing-for-agents/SKILL.md): Guides writing for skills and other agent-facing documents.
- [`unslop`](./skills/productivity/unslop/SKILL.md): Removes AI writing tells and keeps prose concrete.

### Teaching

#### User-invoked

- [`teach`](./skills/teaching/teach/SKILL.md): Teaches a concept over multiple sessions in a stateful workspace.
- [`study-course`](./skills/teaching/study-course/SKILL.md): Guides you through a named week of supplied course material.

## Custom skills

- [`study-course`](./skills/teaching/study-course/SKILL.md): The custom weekly course help workflow. It keeps a plan, attempts, prerequisite gaps, notes, and learning records across sessions while following the course material you provide.
- [`copse`](./skills/engineering/copse/SKILL.md): The custom Copse issue tracker integration for the engineering skills.

## Beta skills

These skills are public but are not included in the plugin. Install them directly with `skills.sh` if you want to try them.

- [`loop-me`](./skills/in-progress/loop-me/SKILL.md): Develops implementable workflow specs over multiple sessions.
- [`writing-beats`](./skills/in-progress/writing-beats/SKILL.md): Shapes an article one beat at a time.
- [`writing-fragments`](./skills/in-progress/writing-fragments/SKILL.md): Mines raw writing fragments for future articles.
- [`writing-shape`](./skills/in-progress/writing-shape/SKILL.md): Shapes raw Markdown into an article paragraph by paragraph.
- [`claude-handoff`](./skills/in-progress/claude-handoff/SKILL.md): Hands work to a fresh background Claude agent.
- [`setup-ts-deep-modules`](./skills/in-progress/setup-ts-deep-modules/SKILL.md): Adds dependency-cruiser boundaries to a TypeScript repository.
- [`implement-spec`](./skills/in-progress/implement-spec/SKILL.md): Implements a spec across a ticket task graph.
- [`retro`](./skills/in-progress/retro/SKILL.md): Suggests improvements to the coding-agent environment. This is currently a stub.

## Utility skills

These skills are kept in `skills/misc/` and are not included in the plugin.

- [`git-guardrails-claude-code`](./skills/misc/git-guardrails-claude-code/SKILL.md): Blocks dangerous Git commands with Claude Code hooks.
- [`migrate-to-shoehorn`](./skills/misc/migrate-to-shoehorn/SKILL.md): Replaces test type assertions with `@total-typescript/shoehorn`.
- [`scaffold-exercises`](./skills/misc/scaffold-exercises/SKILL.md): Creates exercise, problem, solution, and explainer directories.
- [`setup-pre-commit`](./skills/misc/setup-pre-commit/SKILL.md): Configures Husky, lint-staged, formatting, type checking, and tests.

## Development

Keep the manifests, bucket READMEs, docs pages, and skill metadata in sync when adding or moving a promoted skill. Run:

```bash
claude plugin validate . --strict
git diff --check
```

Use [`writing-for-agents`](./skills/productivity/writing-for-agents/SKILL.md) when editing a skill or agent-facing document. Apply [`unslop`](./skills/productivity/unslop/SKILL.md) to prose changes.
