<p align="center">
  <img src="assets/logo.png" alt="OrcaStation logo" width="360">
</p>

# OrcaStation

**A model-agnostic guide and toolkit for orchestrating AI-assisted development.**
Spend your expensive tokens on thinking, not typing.

Maintained by the [AI Game Dev](https://aigamedevs.org) community.

[Website](https://aigamedevs.org) · [Discord](https://discord.gg/GGszfGZg8a) · [Start here](START.md) · [Guide](guide/README.md) · [Cheat sheet](CHEATSHEET.md) · [Worked example](examples/inventory)

![The OrcaStation loop: orchestrator, implementer, reviewer](assets/hero.svg)

---

## What is OrcaStation?

OrcaStation is a resource for learning **orchestration**, a core part of effective AI-assisted development, together with a set of
tools you can use to put it into practice in your own projects, whether they're brand new or already underway.

Orchestration means splitting a development job across **separate AI sessions with distinct roles** (planning, building,
reviewing) that are coordinated through **written handoffs** (specs, reports, reviews) instead of one long conversation. Each job gets
the level of capability it actually needs, and nothing is trusted just because the session that produced it said so.

OrcaStation wraps that idea around a standard, phase-driven software development cycle, along with the practices that make it work:

- Planning in phases, and writing small, specific specs for each task
- Adversarial code review by an independent session
- Tests, or explicit acceptance checks, tied to every task
- Parallel work, with checks to keep tasks from colliding
- Project state kept in files: plans, decisions, and handoffs
- Matching models and effort settings to each role

You'll find a step-by-step [guide](guide/README.md), [playbooks](START.md) for starting a new project, adopting the workflow in an
existing one, or just trying it on a single task, drop-in [agent instructions](AGENTS.md), [templates](templates), and a
[worked example](examples/inventory).

## The problem with one session and one model

Using a single model in a single session is simple, and it works for small jobs. On bigger ones, these problems
tend to show up. Some come from relying on one session, and some from relying on one model.

**From using one session**

- **The builder grades its own work.** When the same session writes the code and the tests, it can write tests that pass
  no matter what the code does, and it tends to agree with its own reasoning. The result can be a test suite that
  always passes without properly evaluating anything.
- **Bloated context.** A long session fills with history that the current task doesn't need. Important details get
  diluted, decisions get forgotten, and quality can drift.
- **State trapped in the conversation.** Decisions and plans live in chat. When the session ends or restarts, they're gone.
- **Vague, oversized tasks.** Asking for a big, loosely defined piece of work in one go invites guessing, scope creep, and rework.

**From using one model**

- **One capability level for every task.** Planning and untangling ambiguity take a lot of capability. Following a clear
  instruction takes much less. A top-tier model on everything burns tokens without extra benefit on the easy parts, while a
  light model on everything struggles with the hard parts. No single choice fits every stage of development.
- **Shared blind spots.** A model reviewing its own work, or that of another session running the same model, tends to
  share the same assumptions and weaknesses, so it can miss the very mistakes it made. A different tier or model can catch
  different things.
- **One set of strengths and limits.** Every model is better at some things than others, and usage limits can stall all of
  your work at once. Relying on a single model leaves no flexibility or fallback.

## The solution

Orchestration gives each job its own session, and its own model where that helps, and ties them together through files.
OrcaStation turns that into a process you can follow.

| Problem | What OrcaStation does |
|---|---|
| One capability level for everything | Match the tier to the task: your strongest model plans and writes specs, and the lightest model that reliably works builds ([Choosing tiers](guide/07-choosing-tiers.md)) |
| Builder grades itself | An independent reviewer in a fresh session checks the result against the spec |
| Bloated context | A fresh session per task, given only the spec and facts it needs |
| Lost state | Plans, specs, decisions, and handoffs live in files, not chat |
| Vague tasks | Small, specific specs, with parallel work only when files and interfaces don't collide |
| Shared blind spots | The reviewer runs in a fresh session, and can be a different tier or model so it doesn't share the builder's assumptions |
| One model's limits | Use several tiers (and vendors, if you like), so you can pick the right tool per task and keep working when one runs low |

### What you get

- **For you:** a way to spend expensive tokens on the work that needs them, a process you can repeat, and less time re-explaining context to a session.
- **For your workflow:** small, well-defined tasks, project state that survives a restart or a handoff, and parallel work when it's safe.
- **For your results:** an independent check on every task, tests or explicit acceptance checks tied to the spec, and decisions on record so the same mistake doesn't come back.

> These are benefits observed in practice, not guarantees. Lighter models need tighter specs, and writing good specs
> costs orchestrator tokens. The guide covers the tradeoffs.

### The three roles

| Role | Job | Tier |
|------|-----|------|
| **Orchestrator** | Plans the project and writes precise specs | Most capable tier |
| **Implementer** | Follows one spec and builds it | Lightest tier that does it reliably |
| **Reviewer** | Independently audits the result against the spec | Strong tier, **fresh session** |

## When to use OrcaStation

### Use it when

- You're building multi-step features or making larger changes
- Correctness matters
- The project will span many sessions, or be handed between people or sessions
- You want to run tasks in parallel
- You keep hitting usage limits, or keep re-explaining context to a session

### It's probably not the right fit when

- You're making a tiny change, like a typo fix, a rename, or a small UI tweak
- You're writing a one-off script
- You're exploring and don't yet know what you want to build

### What it does, and what it doesn't

**It does**
- Teach orchestration and how to apply it
- Give you playbooks, templates, and agent instructions to follow
- Help you match models and effort settings to each role
- Provide a phase-driven workflow with independent review built in

**It doesn't**
- Decide what you should build, or replace your own judgment
- Install software or run agents for you. It isn't a framework, an app, or an agent runtime
- Choose a model for you. The examples are dated snapshots, so check them
- Cover deployment or security audits
- Guarantee savings or correctness

## How to use OrcaStation

Pick the option that matches where you are. Each one has a playbook with step-by-step instructions and copy-paste prompts.
You can follow a playbook yourself, or give [START.md](START.md) to an AI session and let it guide you. If your chat app can't
read files, paste the playbook you want into the session.

### Lite: try it on one task

- **What it is:** the lightest way to use the method, with no setup. A strong model plans and writes a spec, a lighter model builds, and a fresh session reviews.
- **Use it when:** you're trying OrcaStation for the first time, or you have one small-to-medium task in any project or tool.
- **How:** open three separate sessions (orchestrator, implementer, reviewer), and follow [playbooks/lite.md](playbooks/lite.md): plan, write a small spec, build in a fresh session, review in another fresh session, then fix what the review finds.

### New project: build with OrcaStation from the start

- **What it is:** a guided setup for a project that uses the full workflow from day one.
- **Use it when:** you're starting something new and want specs, reviews, and saved project state built in.
- **How:** follow [playbooks/new-project.md](playbooks/new-project.md): choose a stack, create the repo layout with `AGENTS.md` and a `docs/` folder, plan in phases, write specs for the next phase only, then run the build-and-review loop.

### Adopt in an existing project

- **What it is:** a way to add the workflow to a codebase you already have, without changing anything until you approve.
- **Use it when:** you have existing code and want to work on it with OrcaStation.
- **How:** follow [playbooks/adopt-existing-project.md](playbooks/adopt-existing-project.md): set the scope, let the agent look around read-only, review its assessment and recommended level, approve the setup, then plan only the work you're doing.

### Choose models: match models to roles

- **What it is:** a short exercise that decides which model and effort setting fills each role.
- **Use it when:** you're unsure which models to use, or before starting any of the options above.
- **How:** follow [playbooks/choose-models.md](playbooks/choose-models.md): list what you have access to, sort it into tiers, accept or adjust the suggested mapping, and save it to `docs/models.md`. [Choosing tiers](guide/07-choosing-tiers.md) explains the reasoning, and [model examples](reference/model-examples.md) has dated Claude and ChatGPT examples.

### The three levels

| Level | What you use |
|---|---|
| **Lite** | Separate sessions and written specs. No repo files. |
| **Standard** | Lite, plus `AGENTS.md`, a `docs/` folder, saved specs, reports, and reviews, and one branch per task. |
| **Full** | Standard, plus parallel tasks, a models file, and metrics. |

Start with Lite or Standard and move up only when something specific is holding you back. [START.md](START.md) compares the levels in detail.

**Not sure where to begin?** Run Lite on one real task. Or paste [START.md](START.md) into a session, and it will ask three short questions and recommend an option. If you'd rather learn first, start with the [guide](guide/README.md).

## The six principles

1. **One outcome per spec.**
2. **Specs carry the facts.**
3. **Tests first, and make them able to fail.**
4. **Define "done" mechanically.**
5. **Never let the builder grade itself.**
6. **Fresh session per task, state in files.**

## Works with anything

Bring your own models and subscriptions. OrcaStation doesn't depend on a specific model, vendor, or tool. It works with chat apps,
command-line and IDE agents, and parallel-agent environments, as long as your setup lets you run more than one session.
For dated examples with Claude and ChatGPT models, see [model examples](reference/model-examples.md).

## FAQ

**Do I need several different models?** No. One model in separate sessions still gives you fresh context and independent review.
Using different tiers is what adds the token savings.

**Do I need special software?** No. It's a set of files and a way of working.

**Is it only for game development?** No. It comes from a game dev community and the examples are game-flavored, but the method suits any software project.

**How much will I save?** It depends on your work, so we don't promise numbers. Chapter 11 shows how to measure your own.

## What's in this repo

```
OrcaStation/
├── README.md        You are here
├── START.md         Entry point with copy-paste playbooks
├── playbooks/       Step-by-step modes: Lite, new project, adopt, choose models
├── CHEATSHEET.md    One-page summary
├── LICENSE          MIT license
├── AGENTS.md        Drop-in instructions for agents
├── guide/           The full guide, chapter by chapter
├── templates/       Spec and review templates
├── examples/        A worked example, from spec to accepted
├── reference/       Dated model examples
└── assets/          Logo and diagrams
```

In the [worked example](examples/inventory), every automated check passed and the work was still wrong.
An independent review caught it.

## Status

First full draft. Start with the [guide index](guide/README.md), or jump to the [worked example](examples/inventory).

## Help test OrcaStation

OrcaStation is a first draft, and the most valuable thing you can give it is a real test. Try it on a task, then tell us what
worked and where you got stuck.

**[Send a test report](https://github.com/NotHarroweD/OrcaStation/issues/new?template=test-report.yml)** (needs a free GitHub account),
or share your results in the [Discord](https://discord.gg/GGszfGZg8a).

## Community

Questions, results, and war stories are welcome in the [AI Game Dev Discord](https://discord.gg/GGszfGZg8a).
If you try OrcaStation on a real project, we'd love to hear how it went.

## Contributors

Thank you to everyone who has tested OrcaStation and shared feedback. Your input directly improves the benefit this resource provides to the community.

- **ShinyStarSam**: First Tester/Feedback contributor.

Want to be listed? Try OrcaStation on a real project and share what worked and what didn't, in the [Discord](https://discord.gg/GGszfGZg8a) or by opening a [test report](https://github.com/NotHarroweD/OrcaStation/issues/new?template=test-report.yml).

## License

MIT. See [LICENSE](LICENSE).
