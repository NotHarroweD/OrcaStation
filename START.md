# OrcaStation: start here

This is the entry point. You can read it yourself, or give it to an AI session and let the session guide you.
It works with any model or tool.

## Before you let an agent follow this file

- **Read it first.** An agent will do what a file tells it to.
- **Use a copy you trust.** If you're loading it from a URL, use a tagged release or a copy you've checked, not a branch that can change under you.
- **Keep approval in your hands.** The agent should propose actions and wait for your OK before creating files, changing code, or running commands.
- **Chat apps can't read files.** If your session can't open files, paste this file and then the playbook you choose.

## Instructions for the agent

If you are an AI agent that has been given this file:

1. **Don't act yet.** Ask the user which mode they want from the menu below, or help them choose.
2. **Say what you're about to do, and why, in one sentence** before each step. Wait for approval before anything that
   creates, changes, or deletes files, or runs commands.
3. **Never run destructive git commands** (hard reset, force push, clean, stash, rebase), and never push to a remote,
   unless the user explicitly asks.
4. **Don't assume which models the user has.** Ask.
5. **Follow the playbook for the chosen mode,** keeping its human checkpoints.
6. **Keep replies short** and explain jargon briefly the first time you use it.

## Choose a mode

| Mode | Use it when | Playbook |
|---|---|---|
| **Lite** | You want to try the workflow on one task, in any project, with no setup | [playbooks/lite.md](playbooks/lite.md) |
| **New project** | You're starting something new and want OrcaStation built in | [playbooks/new-project.md](playbooks/new-project.md) |
| **Adopt in an existing project** | You have a codebase and want to add the workflow | [playbooks/adopt-existing-project.md](playbooks/adopt-existing-project.md) |
| **Choose models** | You're unsure which model and effort setting should do which job | [playbooks/choose-models.md](playbooks/choose-models.md) |

**Not sure?** Ask the user three questions:

1. Is this a new project or an existing one?
2. Is the next piece of work one small task or many steps?
3. Which models and tools do you have access to?

Then recommend: a small task or a first try means **Lite**; a new project means **New project**;
an existing multi-step project means **Adopt**. Offer **Choose models** whenever the user is unsure about tiers.

## The three levels

| Level | What you use |
|---|---|
| **Lite** | Separate sessions and written specs. No repo files, branches, or saved reports. |
| **Standard** | Lite, plus `AGENTS.md`, the `docs/` folder, saved specs, reports and reviews, and one branch per task. |
| **Full** | Standard, plus parallel tasks, `docs/models.md`, metrics, and sanity-break checks. |

Start at Lite or Standard. Move up only when something specific is holding you back.

## Learn more

- [Guide](guide/README.md): the full explanation
- [Cheat sheet](CHEATSHEET.md): one page
- [AGENTS.md](AGENTS.md): the instructions agents follow in Standard and Full
- [Worked example](examples/inventory): one task from spec to accepted
