---
name: implement
description: "Implement a piece of work based on a spec or set of tickets."
disable-model-invocation: true
---

Implement the work described by the user in the spec or tickets.

When a cheap local test path exists or the user asked for TDD, call the Skill tool with "tdd" at the pre-agreed seam. Otherwise state why you are skipping it.

Run typechecking regularly, single test files regularly, and the full test suite once at the end.

Before review, commit a verified implementation checkpoint to the current branch. The review needs a committed diff against a fixed point. If the change has hidden consumers or runtime risk, call the Skill tool with "blast-radius" before the review. Then call the Skill tool with "code-review" against the pre-implementation fixed point.

Apply accepted findings, rerun the relevant checks, and commit the review fixes. After a complex run or a user correction, ask the user to run `/reflect` so durable lessons can be captured.
