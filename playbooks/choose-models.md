# Playbook: Choose models

**For:** deciding which model and effort setting should do which job.
**Background:** [Chapter 7](../guide/07-choosing-tiers.md) explains the reasoning.
**Agent:** don't assume which models the user has. Ask, and verify anything that may have changed.

## Step 1: List what the user has

Ask the user:

- Which models and tools can you use right now?
- Which effort or thinking settings does your tool offer?
- Are there usage limits (daily, weekly, rolling) you're trying to stay under?
- Do you care more about cost, speed, or quality right now?

## Step 2: Sort them into tiers

- **Top:** the most capable models available to them.
- **Middle:** strong all-rounders.
- **Light:** fast, low-cost models.

If you need current details, check the vendor's own model page. [reference/model-examples.md](../reference/model-examples.md)
has a dated snapshot, but verify it before relying on it.

## Step 3: Propose a mapping

| Role | Suggested starting point |
|---|---|
| Orchestrator | Top tier, higher effort |
| Implementer: standard | Middle tier (if the user is new, start here) |
| Implementer: mechanical | Light tier |
| Implementer: hard | Middle or top tier, with a narrower spec |
| Reviewer | Middle to top tier, higher effort, fresh session, ideally a different model than the implementer |

**If the user has only one model:** use it for every role in separate sessions, with higher effort for the orchestrator
and reviewer if the tool allows.

## Step 4: Confirm and record

Show the user the mapping and adjust it. After approval, write `docs/models.md` (template in Chapter 7), or give
them the table to paste into their notes if they're not using a repo.

## Step 5: Tune over time

After 3 to 5 similar tasks pass on the first try, try the light tier on the next few. If a tier fails on well-written
specs, move that kind of task up. Review the file whenever the available models change.
