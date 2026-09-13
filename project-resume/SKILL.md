---
name: project-resume
description: Resume a project from the handoff file it keeps in its repo. Use when the user says resume, continue, or pick up a project, when starting a session on a project whose history you lack, or when a repo contains a handoff file (HANDOFF.md, CONTEXT.md) you have not read yet.
---

# Project resume

A project that keeps a handoff is meant to be continued from the file, not from the
conversation that produced it — that conversation is gone. Resuming means letting the
file put you where the last session ended, then verifying enough of it to trust the
ground under your feet.

## How to resume

1. **Find the handoff before touching anything else.** Look for `HANDOFF.md` or
   `CONTEXT.md` at the project root; if neither exists, check `README.md`,
   `CLAUDE.md` and `AGENTS.md` for a pointer to wherever the project's memory lives.
   Read the whole file, however long it is — it is the cheapest context you will load
   all session. If the project keeps no handoff, say so, orient from the repo itself,
   and offer to write one (that is the `project-handoff` skill's job).
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
5. **When the file and the world disagree, fix the file in the same session.** A
   handoff that is wrong once gets distrusted entirely, and the next reader repeats
   your verification work. Update it the way the `project-handoff` skill describes.
6. **Start the named next task, not the one you would have guessed.** If it is blocked
   — a missing credential, a decision the human owes — surface the blocker instead of
   silently picking different work.
