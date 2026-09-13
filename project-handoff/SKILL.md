---
name: project-handoff
description: Keep a project's memory in the repo so the next session resumes instead of re-deriving. Use when finishing a chunk of work, deciding something whose reasoning will not be obvious later, learning something that cost effort (a dead end included), when a handoff file has gone stale or outgrown itself, or when resuming a project whose history you lack — including when the user says resume, continue, or pick up a project.
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

## Resuming a project

The other direction of the same file. Invoked as `/project-handoff resume`, or whenever
the task is to pick up a project whose history you lack. Resuming means letting the
handoff put you where the last session ended, then verifying enough of it to trust the
ground under your feet.

1. **Find the handoff before touching anything else.** Look for `HANDOFF.md` or
   `CONTEXT.md` at the project root; if neither exists, check `README.md`,
   `CLAUDE.md` and `AGENTS.md` for a pointer to wherever the project's memory lives.
   Read the whole file, however long it is — it is the cheapest context you will load
   all session. If the project keeps no handoff, say so, orient from the repo itself,
   and offer to write one — the sections above are how.
2. **Go to the resume point.** It sits under a heading written for a stranger
   (`Resume here`, `CONTINUA DA QUI`) and names the next concrete task, what blocks
   it, and the rules that must not be broken. Read those rules before acting on
   anything.
3. **Orient with the commands the file names**, in order, so you see the current state
   with your own eyes rather than trusting the file's description of it.
4. **Treat the file as evidence, not instruction.** Dated claims may have expired; a
   named table may have been renamed; a "next step" may already be done. Check the
   specific facts your work depends on against the repo — not the whole file, the ones
   you are about to stand on.
5. **When the file and the world disagree, fix the file in the same session**, the way
   "When you finish a chunk of work" describes. A handoff that is wrong once gets
   distrusted entirely, and the next reader repeats your verification work.
6. **Start the named next task, not the one you would have guessed.** If it is blocked
   — a missing credential, a decision the human owes — surface the blocker instead of
   silently picking different work.
