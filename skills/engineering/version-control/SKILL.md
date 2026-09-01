---
name: version-control
description: Enforce version control discipline for any engineering task that changes code. Use when starting a new feature, fixing a bug, creating a branch or worktree, committing, pushing, or merging. Ensures isolated worktrees and branches per feature, clean history, and safe merges.
---

# Version Control

This skill is always on for engineering work that touches code. It defines the industry-standard operating procedure for git: one isolated worktree and branch per feature or fix, main stays clean, history stays readable, merges stay safe.

Consult this before you edit, commit, or push. Work that starts on the wrong branch contaminates history and wastes review time, so the check happens up front, not after.

## Principles

* Main is protected. Never commit directly to `main` or `master`. All work happens on a branch in its own worktree.
* One worktree and branch per unit of work. A new feature, bug fix, or chore gets its own isolated worktree. Parallel work means parallel worktrees, never interleaved edits on one checkout.
* History is a communication tool. Small, atomic commits with clear messages. No fixup noise in the final history.
* Merge only what is reviewed and rebased. The worktree is rebased on latest main, tests pass, review is done, then merge.

## Before you touch code

Run this check every time:

1. Where am I? `git status`, `git branch --show-current`, `git worktree list`, `git log --oneline -5`.
2. Is this the right worktree and branch for this task? If the task is a new feature or fix and you are on `main` or on a worktree for a different feature, stop.
3. Is main up to date? `git fetch origin` and check `main` is not behind.
4. Create the isolated worktree if needed.

Do not edit files until the worktree and branch are correct.

## Creating an isolated worktree

Use `git worktree` for isolation, not just `git checkout -b` in the same directory. Worktrees give you a separate working directory per branch, so you can keep main clean and run parallel tasks without stashing.

From the primary worktree:

```bash
git fetch origin
git worktree add ../<repo>-<slug> -b <type>/<ticket>-<slug> origin/main
# example: git worktree add ../myapp-add-search -b feature/123-add-search origin/main
```

Where:

* `../<repo>-<slug>` is a sibling directory to the primary clone, named for the feature.
* Branch name is `<type>/<ticket>-<slug>` where `type` is `feature`, `fix`, `chore`, or `docs`. Include the ticket number when one exists, for example `feature/123-add-search` or `fix/456-null-crash`.

If the repo already has a convention for branch naming in `CONTRIBUTING.md` or `AGENTS.md`, that convention wins.

To list and remove worktrees:

```bash
git worktree list
git worktree remove ../<repo>-<slug>  # after the branch is merged and pushed
git branch -d <type>/<ticket>-<slug>  # clean up local branch if not already deleted
```

Never create a worktree inside another worktree. Keep them as siblings.

## Branch and commit discipline

* One branch per ticket or spec. Do not pile unrelated changes onto one branch.
* Keep branches short-lived. Rebase on `main` often, do not let them drift.
* Commits are atomic. One logical change per commit. A commit builds and passes tests on its own.
* Commit messages reference the ticket when one exists: `feature: add search (#123)` or `fix: handle null in checkout (#456)`. Follow the repo's existing message style if one is documented.
* Do not commit generated files, secrets, or `.env`. Check `.gitignore` before adding.
* Do not use `git commit --no-verify` or `git push --force` without explicit user approval. If you must force-push after a rebase, use `git push --force-with-lease`.

## While you work

* Stay in the worktree for this task. Do not edit the same files from a different worktree.
* Commit regularly in the worktree. Push the branch to `origin` to back it up: `git push -u origin <branch>`.
* Before you finish, sync with main:

```bash
git fetch origin
git rebase origin/main
# resolve conflicts by intent, then
git push --force-with-lease
```

* Run the repo's tests and typechecks before you ask for review. A failing branch wastes reviewer time.

## Merging

* Merge through a pull request or the repo's documented method, not by merging locally into main and pushing main.
* The worktree branch is reviewed via `/code-review` and any required CI checks before merge.
* After merge, clean up:

```bash
git fetch origin
git worktree remove ../<repo>-<slug>
git branch -d <branch>  # if still present locally
git fetch --prune
```

* Delete the remote branch when the hosting platform does not do it automatically.

## When not to create a new worktree

* Docs-only or single-file chores with no ticket and no risk of parallel work can use a branch in the current worktree. Still never work on main.
* Trivial hotfixes that must go out now can branch directly from the release tag, but still in a fresh worktree.
* If the user explicitly asks to work on main in a solo repo with no protection, confirm it back to them and note the exception.

## Relation to other skills

This skill controls where and how code changes happen. It does not replace `/tdd` for how they are built or `/code-review` for how they are checked. A typical sequence is: this skill decides the worktree and branch, `implement` drives `tdd` per ticket inside that worktree, `code-review` checks the branch, then this skill governs the rebase and merge. If you hit a conflict during rebase, call the Skill tool with "resolving-merge-conflicts".
