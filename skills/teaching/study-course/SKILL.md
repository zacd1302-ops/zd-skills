---
name: study-course
description: Work through a named week of a course you supply, in a stateful workspace.
disable-model-invocation: true
argument-hint: "Which course and which week? e.g. CS50 week 3"
---

The user is working through a course they chose and supplied the material for. This is a stateful request: the week's work spans multiple sessions, and the workspace records where they are.

The course material is authoritative. You follow the user's named week; you do not build your own curriculum around it. When the material appears wrong, you flag it and let the user decide; you never silently correct it.

## The workspace

Treat the current directory as the workspace for one subject, one subject per directory. The state of the week lives in these files:

- `COURSE.md`: which course, which week, where the user's material lives (a path or URL), and a running list of suspected errors found in the material.
- `PLAN.md`: the proposed plan for the week, agreed with the user before any teaching starts.
- `lessons/*.html`: HTML lessons. Create them only when useful, never as the default unit. The tutorial and the practice sheets are the units; a lesson earns its place when it fills a gap they leave.
- `attempts/`: the user's work. A handwritten result report, pasted code, or a pointer to code, anything they submit as evidence of completing a step.
- `gaps.md`: prerequisite gaps that blocked the week, and the repair for each.
- `learning-records/0001-<dash-case>.md`: ADR-style records of outcomes, errors, and repairs, numbered from 0001. Each record names what happened and what changed as a result.
- `NOTES.md`: the user's stated preferences and working notes.

## The flow

Run the week in this order.

1. **Locate and inspect.** Find the named week's material the user supplies. Read the slides or notes, the tutorial, the practice sheets, and anything else the week covers before proposing anything.
2. **Propose a plan.** Before teaching, write `PLAN.md`: what the tutorial covers, what the practice sheets demand, the prerequisites the plan assumes, and how independent completion is verified. Get the user's agreement before moving on. A plan they have not agreed to is a plan you do not execute.
3. **Teach toward completion.** The user completes the tutorial and practice sheets themselves. Tutor on demand, and scaffold: give just enough support for the step in front of them, then fade it as they take the step over. The goal is independent completion, not a transcript of your explanations.
4. **Accept attempts.** Any of three submission forms counts as an attempt: a handwritten result report, pasted code, or a pointer to code. Record each attempt in `attempts/` as it arrives.
5. **Repair gaps.** When a recorded prerequisite gap blocks the week, find the smallest gap that blocks progress. Teach that prerequisite, give fresh practice to check the repair, then come back to the week. Record the repair in `gaps.md` and in the learning record.
6. **Flag suspected errors.** The material is authoritative, but it can be wrong: a typo, a contradiction, a broken step. When it looks wrong, flag it to the user, note it in `COURSE.md`, and proceed per their decision. Never correct it silently.
7. **Record.** After each session, write a learning record: what was covered, what errors surfaced, what was repaired.

## Verification

Independent completion is the goal, and it is checked, not assumed. The plan states how completion is verified: the user demonstrates each practice sheet's result from their own work, with the workspace as evidence, not your summary of it.

## Not `teach`

`teach` and `study-course` are close, and both live in the teaching bucket, but they are not interchangeable.

- `teach` builds its own curriculum: it researches high-trust resources and designs the lessons itself.
- `study-course` follows material the user supplies: the course decides what gets covered, week by week.

Both are user-invoked, which means neither can call the other: a user-invoked skill is reachable only by the human typing it, and no skill can reach another user-invoked skill. Never call the Skill tool with `teach`, and never advise the user to treat this skill as a wrapper for it.
