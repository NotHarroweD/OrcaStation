# Playbook: New project

**For:** starting a project with OrcaStation built in, at the **Standard** level.
**You need:** a place to put a repo, and sessions for the orchestrator, implementer, and reviewer roles.

**Agent:** propose each step and wait for approval before creating anything.

## Step 1: Understand the project

Ask the user: what are you building, who is it for, and what does "working" look like for a first version?
Ask which models they have, or run [choose-models](choose-models.md) first.

## Step 2: Choose the stack

Propose two or three options and explain the tradeoffs. Good choices for this workflow:

- everything runs from the command line, with no manual steps to verify work;
- one command can run all checks (tests, lint, type checks);
- tests run in seconds;
- the tools are popular and well documented;
- few moving parts;
- core logic can be separated from presentation, so it can be tested without a window or engine.

Let the user decide, and record the choice.

## Step 3: Set up the repo

Propose this layout, then create it after approval:

```
project/
├── AGENTS.md          Copy from the OrcaStation repo, unedited at first
├── check              One command that runs all checks (it should pass even with no tests yet)
├── src/
├── tests/
└── docs/
    ├── plan.md
    ├── specs/
    ├── reports/
    ├── reviews/
    ├── decisions.md
    ├── handoff.md
    └── models.md      From the choose-models playbook
```

Make the first commit. Use one branch per task from here on.

## Step 4: Plan in phases

Orchestrator session. Prompt:

> You are the orchestrator. Read AGENTS.md. Here is the project: <summary and stack>.
> Write docs/plan.md: Phase 0 is the skeleton (repo, check command, one passing test), then thin working slices,
> then depth. Break each phase into tasks that each have one outcome, and note dependencies and which tasks could run
> in parallel. Don't write specs yet.

The user reads and adjusts the plan. This is the most valuable thing the orchestrator produces.

## Step 5: Spec only the next phase

> Write specs for Phase 0 only, using templates/spec.md. One file per task in docs/specs/.

## Step 6: Run the loop for each spec

1. **Implement:** fresh session, role and AGENTS.md and one spec. The implementer saves its report to `docs/reports/`.
2. **Review:** fresh session, spec and result, not the implementer's report. The reviewer saves `docs/reviews/`.
3. **Decide (orchestrator):** accept, send back with numbered fixes, or rewrite the spec.
4. **Merge** after the review passes.

## Step 7: Close the phase, then repeat

Orchestrator updates `docs/plan.md` and `docs/decisions.md` and writes `docs/handoff.md`. Then spec the next phase,
using what the last one taught you.
