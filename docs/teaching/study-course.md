## What it does

`study-course` walks you through one named week of a course you supply, toward completing its tutorial and practice sheets yourself, across as many [sessions](https://www.aihero.dev/ai-coding-dictionary/session) as the week takes.

The course material is authoritative. The skill follows your week and your material; it does not build its own curriculum around the topic the way [teach](https://aihero.dev/skills-teach) does. What it adds is the discipline of working the week: a plan agreed before teaching starts, recorded attempts, repaired prerequisite gaps, and a running list of suspected errors in the material, each one raised with you rather than silently corrected.

## When to reach for it

You invoke this by typing `/study-course`; the [agent](https://www.aihero.dev/ai-coding-dictionary/agent) won't reach for it on its own.

Reach for it when you have a course with set material, slides or notes, a tutorial and practice sheets, and you want to actually complete a week of it rather than skim it. The skill's job is to keep you moving through the material and to catch you when a step assumes something you do not have.

| What you want | What to reach for |
| --- | --- |
| To work through a named week of a course you supply | `study-course` |
| To learn a topic with no set curriculum, built from researched resources | [teach](https://aihero.dev/skills-teach) |
| One idea explained inside the session you are already in | Just ask, in that session |
| To sharpen thinking you already have, rather than acquire new material | [grill-me](https://aihero.dev/skills-grill-me) |

## Prerequisites

`study-course` needs the material to follow: a path or URL to the course, the week you want to work, slides or notes, and tutorial and practice sheets. It is also [stateful](https://www.aihero.dev/ai-coding-dictionary/stateful), so run it in a directory you are happy to give over to the subject: `COURSE.md`, `PLAN.md`, `attempts/`, `gaps.md`, `learning-records/` and `NOTES.md` accumulate there, and that state is what lets the next session pick the week up.

## The plan comes first

The word to think with is **plan**. Before it teaches anything, the skill writes `PLAN.md`: what the tutorial covers, what the practice sheets demand, the prerequisites the plan assumes, and how independent completion is verified. Nothing is taught until you agree to it. That gate is what separates working through a course from being lectured at.

From there it scaffolds, just enough support for the step in front of you, fading as you take each step over. Your work goes into `attempts/` as a handwritten report, pasted code, or a pointer to code, and each session ends with a learning record.

## Common questions

**Do I paste the whole course into the chat?**

No. Give it a path or a URL in the invocation, and it locates the named week's material from that.

**What happens when the course material is wrong?**

It flags the suspected error to you, records it in `COURSE.md`, and follows your decision. It never silently corrects the material.

## It's working if

- The first session ends with a `PLAN.md` you agreed to, not a lesson.
- You finish the tutorial and the practice sheets yourself, with the support fading as you go.
- Every attempt you submit lands in `attempts/`.
- A blocked week shows the smallest gap repaired and checked with fresh practice in `gaps.md` before the course work resumes.
- Suspected errors in the material appear in `COURSE.md` and were raised with you.
- `learning-records/` grows one file per session.

## Where it fits

`study-course` is a **reach-for-it-anytime standalone**. It is not a step in the build chain; it owns a directory and works through one week at a time.

Its one real neighbour is [teach](https://aihero.dev/skills-teach), the other teaching skill, because both run a stateful learning workspace: `teach` when you need a curriculum built for you, `study-course` when the course decides the curriculum. When you are not sure which skill or flow fits, [ask-zac](https://aihero.dev/skills-ask-zac) routes you over the whole set.
