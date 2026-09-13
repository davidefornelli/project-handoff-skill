# project-handoff

An agent skill that keeps a project's memory in the repo, so the next session resumes the
work instead of re-deriving how it got there.

It answers the question every long-running project eventually fails at: a session ends,
the reasoning evaporates, and the next one repeats a measurement that was already made or
retries an approach that was already abandoned.

## Install

```bash
npx skills add davidefornelli/project-handoff-skill
```

Lands in `.claude/skills/` (or your agent's equivalent).

## What it does

Splits a project's memory by the three questions it has to answer, because they age at
different rates and mixing them is what makes handoffs rot:

| Question | Goes stale when |
|---|---|
| How does it work now? | the code changes |
| Why is it this way? | almost never |
| Where do I resume? | every session |

Then it sets the bar for what gets written down. The rules that matter most:

- **Record the measurement, not the conclusion.** "Geocoding town names is unreliable"
  invites a rerun; "a search for `Macerata,Italy` returns the province centroid, 28.5 km
  from the town" can be checked and can expire honestly.
- **Record the dead ends**, or they get tried again.
- **Negative results are results** — an absence someone spent a day establishing is a
  finding, not a gap.
- **Scope a rule to the reason it exists**, or it blocks work it was never meant to.
- **Verify the edit landed** — a find-and-replace that matches nothing reports success.

Plus what a resume point owes a reader with no context, when to split one file into two,
and how to read a handoff you did not write.

## Where it came from

Extracted from a long-running scraping project, after enough sessions to see which parts
of a handoff were still load-bearing months later and which had quietly gone stale.

## Licence

MIT
