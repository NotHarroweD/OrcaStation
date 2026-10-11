# Chapter 12: Choosing tiers

**In one line:** put your strongest model where judgment is needed, and the lightest model that works where the job is already spelled out.

This is the question beginners ask most: *which model should do which job?*

## The common mix-up

A natural instinct is: "Implementation is the hard part, so my strongest model should write the code."

It feels right, but it works against you. The hard part of a project is **deciding** what to build and how to break
it up: weighing tradeoffs, closing ambiguity, spotting risks. That's where a strong model earns its cost, and it
costs relatively few tokens because the output is a short plan and a few specs.

Once a spec exists, building it is a **bounded job**: the facts are supplied, the files are named, the tests are listed.
A lighter model can follow that. A strong model writing every line of code spends the most tokens on the part that
needs the least judgment.

## Three tiers

- **Top tier:** the most capable models you have access to. Best at planning, ambiguity, and hard debugging.
- **Middle tier:** strong all-rounders. Good at well-specified building and careful review.
- **Light tier:** fast, cheap models. Good at narrow, mechanical, clearly specified work.

Many tools also let you set how hard a model thinks (often called reasoning or thinking effort).
Treat that setting as part of the tier: the same model on a low setting can fill a lighter role, and on a high setting
a heavier one. More thinking costs more tokens, so raise it on purpose.

## Matching tasks to tiers

| Task looks like | Start with |
|---|---|
| Rename things, boilerplate, apply a known pattern, simple tests | Light |
| A clearly specified function or feature with straightforward tests | Middle |
| Debugging an unclear failure, algorithms, security-sensitive code, unfamiliar APIs | Middle or top, with a narrower spec |
| Planning, writing specs, resolving conflicting requirements | Top |

## Default role assignments

| Role | Default | Why |
|---|---|---|
| **Orchestrator** | Top tier, higher thinking effort | Judgment and spec quality drive everything downstream |
| **Implementer** | Middle tier to start; light tier for mechanical tasks | The spec does the heavy lifting |
| **Reviewer** | Middle to top tier, higher effort, fresh session | Weak reviewers miss subtle problems; using a different model than the implementer can catch different things |

## If you're new, start one step above the cheapest

The usual advice is "start cheap and move up." When you're learning, though, you can't tell whether a failure came from
your spec or from a model that's too weak. Starting the implementer in the **middle tier** lets you learn spec-writing
first. Then tune down:

1. Run 3 to 5 similar tasks with the middle tier.
2. If they pass first time, try the light tier on the next 3 to 5.
3. If the light tier fails, check the spec before blaming the model (Chapter 9), then move back up for that kind of task.

Repeat over time. You're finding the **lightest tier that reliably passes** for each kind of task.

## Signs to move up or down

- **Move up** when well-written, small specs keep failing, or the work needs deep reasoning (debugging, algorithms, security).
- **Move down** when tasks pass first time and the reviewer finds little, which suggests the spec is doing the work.

## If you only have one model

Use it for every role, in **separate sessions**. Fresh sessions and independent review help even without a cheaper tier.
If your tool has an effort setting, run the orchestrator and reviewer higher and the implementer lower.

## Write your choices down

Keep a small file so every session and every teammate uses the same mapping. Put it at `docs/models.md`:

```
# Models

| Role / task type        | Model          | Effort setting |
|-------------------------|----------------|----------------|
| Orchestrator            |                |                |
| Implementer: standard   |                |                |
| Implementer: mechanical |                |                |
| Implementer: hard       |                |                |
| Reviewer                |                |                |

Last reviewed: <date>
```

Review it whenever your available models change.

## Real examples

Model names and offerings change often, so they're kept out of this chapter.
See [`reference/model-examples.md`](../reference/model-examples.md) for dated examples using the Claude and ChatGPT families.

## Do this

Fill in `docs/models.md` for your own setup, starting the implementer one step above the cheapest tier.

**Back to:** [Guide index](README.md)
