---
name: copse
description: Use when configuring or operating the Matt Pocock engineering skills with Copse as the local issue tracker. Defines Copse issue files, links, statuses, labels, and the limits of its read-only board.
---

# Copse

Use Copse as the local issue tracker when a repository has a `.copse/` directory and the user wants the engineering skills to publish issues there.

Copse is a read-only terminal board. The agent creates and updates its Markdown records directly. Running `copse` displays the records, worktrees, and links; it does not replace the file operations below.

## Repository layout

Copse stores records in the primary worktree:

```text
.copse/issues/<uuid>.md
.copse/links/<uuid>.md
```

A linked worktree shares the primary worktree's `.copse` directory. Never create a second `.copse` directory in a linked worktree.

Create the directories only when the user asks to create the first record or link. Starting Copse alone has no side effects.

## Issue records

Every issue file starts with strict TOML front matter delimited by `+++`:

```markdown
+++
id = "11111111-1111-4111-8111-111111111111"
title = "Improve startup time"
status = "open"
labels = ["enhancement", "ready-for-agent"]
+++

## What to build

Issue body in Markdown.
```

Rules:

- Generate a new UUID for every issue.
- Use the UUID as the filename, with a `.md` suffix.
- Use only `open`, `closed`, or `archived` for `status`.
- Store triage labels in the TOML `labels` array. Keep exactly one category label and one state label.
- Preserve unknown front matter keys and the body when editing an existing record.
- Refuse to overwrite a malformed record. Report its path and error instead.
- Keep the issue body in Markdown. Put `Blocked by` and `Parent` references in the body when those relationships apply.

Copse accepts unknown front matter keys, but the board only relies on `id`, `title`, and `status`. Do not treat an extra key as a feature unless this skill or the installed Copse version documents it.

## Worktree links

Create a link only when an issue is assigned to a worktree:

```markdown
+++
id = "22222222-2222-4222-8222-222222222222"
issue = "11111111-1111-4111-8111-111111111111"
worktree = "/absolute/path/to/worktree"
+++
```

Use a new UUID for the link. `issue` points to the issue UUID. `worktree` is an absolute path. Agent state comes from Herdr and is not persisted in the link file.

## Skill operations

When another skill says to publish or fetch a ticket, use the Copse records:

| Operation | Copse action |
| --- | --- |
| Create an issue or spec | Write `.copse/issues/<uuid>.md` with `status = "open"` and the required body. |
| Read an issue | Find the record by UUID or title and read the full file. |
| Add a comment | Append it under `## Comments` in the issue body. |
| Close an issue | Change `status` to `closed`; preserve the body and front matter. |
| Archive an issue | Change `status` to `archived`; do not delete the file. |
| Assign a worktree | Write a matching `.copse/links/<uuid>.md` record. |
| Find ready work | Read open issues, keep those with `ready-for-agent`, then exclude issues whose `Blocked by` references an open issue or whose link already assigns a worktree. |

Use the triage labels configured in `docs/agents/triage-labels.md`. Do not invent Copse-specific label names when the repository already has a mapping.

## Limits

Copse does not write to GitHub Issues. Copse's Map view reads GitHub-backed Wayfinder maps, so local Copse records cannot provide a native Wayfinder map or native blocking edge. For Copse-only repositories:

- Keep `Blocked by: <uuid>, <uuid>` in the child issue body.
- Keep parent relationships in a `Parent: <uuid>` line or section.
- Treat `.copse/issues/` as the source of truth for issue state.
- Do not claim that a Copse record has a native dependency or sub-issue relationship.
- If the user needs a Wayfinder map, use the GitHub tracker or the local Markdown tracker instead, unless a later Copse version documents map support.

## Verification

After creating or editing records:

1. Parse the TOML front matter.
2. Confirm every issue filename is a UUID with a `.md` suffix.
3. Confirm every link points to an existing issue and an existing worktree.
4. Run `copse` or `copse --help` when the binary is available. A missing binary does not invalidate the records.
5. Report any check that could not run.

If the user asks how Copse displays the records, read the repository's Copse documentation or run `copse --help`. Do not infer write commands from the board UI; the current board is read-only.
