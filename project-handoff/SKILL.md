---
name: project-handoff
description: Keep a project's memory in the repo so the next session resumes instead of re-deriving. Use when finishing a chunk of work, deciding something whose reasoning will not be obvious later, learning something that cost effort (a dead end included), or when a handoff file has gone stale or outgrown itself.
---

# Project handoff

A **handoff** is the file a cold reader opens to continue work without the conversation
that produced it. It answers three questions, and keeping them apart is what stops it
rotting:

| Question | Content | Goes stale when |
|---|---|---|
| How does it work now? | the pipeline, the schema, the commands | the code changes |
| Why is it this way? | decisions, and the evidence that settled them | almost never |
| Where do I resume? | the next concrete action | every session |

Mixing them is the common failure: a "how it works" paragraph carrying a buried rationale
gets rewritten when the code changes, and the reasoning dies with it.

## When you finish a chunk of work

Write the handoff before the session ends, while the reasoning is still in context. Later
you will have only the diff, and the diff never says why.

1. **Update how it works** — only the parts the change touched.
2. **Add the rationale for anything non-obvious you decided**, with the evidence (below).
3. **Move the resume point** to the next concrete action.
4. **Reread what you wrote as a stranger.** Every proper noun a cold reader cannot resolve
   is a gap: a table name, a flag, a host, a person. Name the file or the command.
5. **Verify the edit landed.** A find-and-replace that matches nothing usually reports
   success. Grep for the text you just wrote; a handoff that silently failed to save is
   worse than none, because you will trust it.

Done when a reader who has never seen the project can run the next step from the file
alone.

## What makes an entry survive

**Record the measurement, not the conclusion.** "Geocoding bare town names is unreliable"
teaches nothing and invites a rerun. "A free search for `Macerata,Italy` returns the
*province* centroid, 28.5 km from the town, because Nominatim ranks county above comune"
is checkable, and tells the next reader exactly when it stops applying.

**Record the dead ends.** What was tried and abandoned is as valuable as what shipped,
because otherwise it gets tried again. Name the approach and the specific way it broke: a
brand-name matcher that read a catering supplier as a staffing agency, and matched "BMW
Group" on the fragment "w group".

**Negative results are results.** "Three of the largest advertisers have no filings under
those names" is a finding about the world, not a hole in the work. Write it as a finding,
or someone will spend a day rediscovering the absence.

**Date the numbers.** "19 of 21 coordinates land in the comune they claim (2026-09-12)"
ages honestly. "Coordinates are mostly right" cannot be checked, refuted, or retired.

**Scope a rule to the reason it exists.** A rule written wider than its rationale will
either block work it was never meant to block, or get broken quietly. "No browser" made
sense for one site whose API carried everything its pages did; stated flatly, it also
forbade reading sites that have no API at all. Write the boundary and the because.

**Give the hard constraints their own section.** Anything a cold reader cannot derive and
must not violate — a host that forbids this agent, a paid service ruled out, data that is
not reproducible — belongs in one list with the reason beside each. Buried in prose, it
reads as background.

## The resume point

A distinct thing from the rest of the file, because it is aimed at someone with zero
context. Put it under a heading a stranger will find (`Resume here`, `CONTINUA DA QUI`)
and lead the file with a pointer to it.

It carries four things:

- **How to orient**: the commands that show current state, in order.
- **The next task, named concretely** — the file to create, the seam to follow, the
  existing example to copy. "Improve coverage" is not a task.
- **What blocks it**: the credential to obtain, the decision the human owes you, the thing
  that must be verified first.
- **The rules that must not be broken**, or a pointer to them.

## When one file becomes two

Split when the file stops being readable in one pass, and split by question, never by
chronology. A pipeline description and a research log have different lifetimes: one is
rewritten whenever the code moves, the other stays true for years. A dated changelog is
the wrong axis — nobody reads a project's memory in the order it happened.

Leave a pointer both ways, and say in one line what the other file answers, so choosing
between them costs nothing.

## Reading a handoff you did not write

That is the `project-resume` skill's job — invoke it. What matters on the writing side
is the contract it holds you to: the reader will check the facts the work depends on,
and when the file and the world disagree they will fix the file, so write the file as
something worth that trust.
