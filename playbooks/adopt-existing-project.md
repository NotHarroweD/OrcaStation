# Playbook: Adopt in an existing project

**For:** adding OrcaStation to a codebase that already exists.
**Agent:** the assessment in Steps 1 to 3 is **read-only**. Don't create, change, or delete anything until the user approves in Step 4.

## Step 1: Set the scope

Ask the user what they want to do (a feature, a refactor, a bug area) and which part of the project it touches.
Say clearly: "I'll look around first and won't change anything."

## Step 2: Look around (read-only)

Find out, and note briefly:

- what the project is and how it's laid out, and the languages and tools it uses;
- how to run it, and how to run its tests or other checks from the command line;
- whether the tests exist, pass, and run quickly, especially in the area the user will touch;
- any existing AI instruction files, contributor guides, or CI configuration;
- the git state: current branch, and whether the working tree is clean.

## Step 3: Write the assessment

Give the user a short report:

1. **Summary:** what the project is and what you found.
2. **Checks:** is there a single command that runs the checks? If not, what would it be?
3. **Test health** in the area of interest.
4. **Risks:** anything that could make this work harder (no tests, tangled areas, slow checks).
5. **Recommended level** (Lite, Standard, or Full), with reasons.
6. **Proposed setup:** which files would be added or changed. Never overwrite an existing instruction file; propose
   pointing it at `AGENTS.md` or merging by hand.
7. **First tasks:** one to three small, bounded tasks. If there are no tests where the work will happen,
   the first task is "write tests that capture current behavior."
8. **Questions** for the user.

## Step 4: Wait for approval

Don't modify anything until the user says yes. They may change the level or the first tasks.

## Step 5: Set up (after approval)

- Create a branch for the setup.
- Add `AGENTS.md` and the `docs/` folders, and a `check` command that wraps the existing tests.
- Commit the setup on its own.
- Run [choose-models](choose-models.md) if the user wants `docs/models.md`.

## Step 6: Plan only what's in scope

Write `docs/plan.md` for the user's goal, not for the whole codebase. Spec the first task only, then run the loop
from [new-project](new-project.md), Step 6. Avoid opportunistic refactoring: each spec has one outcome and a short
allowed-files list.
