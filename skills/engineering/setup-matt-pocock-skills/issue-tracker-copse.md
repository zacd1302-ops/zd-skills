# Issue tracker: Copse

This repository uses [Copse](https://github.com/zacd1302-ops/copse) as its local issue tracker. Copse displays issue records from the primary worktree's `.copse/` directory.

## Conventions

- Issues live at `.copse/issues/<uuid>.md`.
- Worktree links live at `.copse/links/<uuid>.md`.
- Issue files use `+++`-delimited TOML front matter with `id`, `title`, and `status`.
- Valid issue statuses are `open`, `closed`, and `archived`.
- Add triage labels in a TOML `labels` array. Keep exactly one category label and one state label.
- Use UUID filenames and generate a new UUID for every issue and link.
- Keep `Blocked by: <uuid>, <uuid>` and `Parent: <uuid>` in the Markdown body when those relationships apply.
- Append comments under `## Comments`.
- The primary worktree owns `.copse`; linked worktrees share it.

## When a skill says "publish to the issue tracker"

Create or update the relevant `.copse/issues/<uuid>.md` record. Preserve valid existing front matter, unknown keys, and the body when editing. Refuse to overwrite malformed records.

## When a skill says "fetch the relevant ticket"

Find the issue record by UUID or title and read the full file, including comments.

## Frontier

An issue is ready when it has `status = "open"`, the `ready-for-agent` label, no assigned `.copse/links/` record, and no open issue named in its `Blocked by` line. A blocker is closed when its issue record has `status = "closed"`.

## Relationships and Wayfinder

Copse records do not provide native blocking or parent-child relationships. Store those relationships in the issue body using UUIDs. Copse's Map view reads GitHub-backed Wayfinder maps, so do not create a local Copse record and claim it is a Wayfinder map. Use the local Markdown tracker or GitHub when a Wayfinder map is required.

## Verification

After writing records, parse the TOML front matter, check UUID filenames, check that links point to existing issues and worktrees, and run `copse` or `copse --help` when the binary is available. Report checks that could not run.
