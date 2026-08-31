## What it does

`copse` defines how the engineering skills use [Copse](https://github.com/zacd1302-ops/copse) as a local issue tracker. It gives the agent the issue file format, UUID and status rules, triage labels, worktree links, and relationship conventions.

Copse's board is read-only. The agent writes issue and link records directly, then Copse displays them from the primary worktree.

## When to reach for it

Type `/copse`, or the agent reaches for it automatically when a repository uses `.copse/`. Reach for it when configuring the engineering skills for Copse or when publishing, reading, closing, or linking Copse issues. For the setup flow, use [setup-matt-pocock-skills](https://aihero.dev/skills-setup-matt-pocock-skills).

## Records and relationships

Issues live at `.copse/issues/<uuid>.md` with TOML front matter delimited by `+++`. Links live at `.copse/links/<uuid>.md`. Copse supports `open`, `closed`, and `archived` issue statuses. Blocking and parent relationships live in the Markdown body because Copse does not provide native dependency or sub-issue records.

## It's working if

- Every issue has a UUID filename, valid TOML front matter, a title, and a supported status.
- Triage labels use the repository's configured mapping.
- A linked worktree has an absolute path and points to an existing issue.
- The agent does not claim that a local Copse record is a native Wayfinder map.

## Where it fits

`copse` is a model-invoked engineering reference used by [setup-matt-pocock-skills](https://aihero.dev/skills-setup-matt-pocock-skills) and the tracker-dependent skills. It complements [to-spec](https://aihero.dev/skills-to-spec), [to-tickets](https://aihero.dev/skills-to-tickets), and [triage](https://aihero.dev/skills-triage), which publish or process the records. [ask-zac](https://aihero.dev/skills-ask-zac) routes across the full set.
