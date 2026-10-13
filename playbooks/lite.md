# Playbook: Lite

**For:** trying OrcaStation on one task, in any project, with no setup.
**You need:** three separate sessions (separate chats or agent runs): orchestrator, implementer, and reviewer. They can all use the same model. See [choose-models](choose-models.md) if you're
unsure which models to use. If you only have one model, use it in all sessions.
**Time:** a very small task can take around 20 minutes once you know the workflow. Expect longer while you're learning it, or for tasks that need real investigation.

No `AGENTS.md`, branches, or saved reports are needed. Paste the prompts below into the sessions.

## Step 1: Plan (session A, your strongest model: the orchestrator)

> You are the orchestrator. I'm working on: <describe your project and goal>.
> Ask me any questions you need, then give me a short plan: the smallest next piece of work, and how we'll know it's done.

Read the plan and push back before moving on.

## Step 2: Write the spec (still session A)

> Write a spec for that first piece of work that a different AI session can follow with no other context. Include:
> why it matters, which files it may touch, exactly what to build, the facts it needs (names, constraints, decisions),
> which tests to write first and what change should make the key ones fail, the exact commands to check the work,
> and what's out of scope. Keep it short.

If the spec feels big, ask the orchestrator to split it.

## Step 3: Build (session B, fresh: the implementer)

If you're new, use a model one step above your cheapest. Paste the spec, then:

> You are the implementer. Do exactly what this spec says and nothing else. Write the tests first and confirm they fail,
> then implement, then run the checks. If the spec is impossible or unclear, stop and tell me why. When done, report what
> you changed, the test and check results, and anything you're unsure about.

## Step 4: Review (session C, fresh: the reviewer)

Paste the spec and the actual result (the changed files or diff). **Do not paste the implementer's report.**

> You are the reviewer. You didn't write this. Find problems; don't approve by default and don't fix anything.
> Check that it meets the spec, that the checks pass, and that nothing outside the spec changed.
> For the one or two most important tests, say what change to the code should make each fail, and whether the test
> would really notice. List problems with file and location, and tell me if the spec itself looks wrong or incomplete.

## Step 5: Fix or accept

If the reviewer found problems, open a **fresh** implementer session. Give it the spec and a numbered list of exactly what
is wrong, and nothing else. Review again. When it's clean, you're done with that task. Repeat from Step 2 for the next one.

## What next

- Did the reviewer find something the implementer missed? That's the workflow doing its job.
- Did the spec work? If a session guessed or wandered, tighten the spec.
- Ready for more structure? Try [new-project](new-project.md) or [adopt-existing-project](adopt-existing-project.md).
