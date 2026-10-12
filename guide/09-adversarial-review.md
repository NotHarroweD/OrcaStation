# Chapter 9: Adversarial review

**In one line:** a reviewer who didn't write the code, and is told to find problems, catches what checks can't.

## Why checks aren't enough

Automatic checks catch what you thought to test. A reviewer catches what you didn't: tests that can't fail,
quietly weakened assertions, scope creep, edge cases nobody wrote down.

## What makes a review independent

- **A fresh session.** No shared history with the implementer.
- **It sees the spec and the real result.** Not the implementer's summary of what it did.
  If the reviewer reads the builder's own account first, it tends to agree with it.
- **Its job is to find problems.** "Is this good?" invites a yes. "What's wrong with this?" doesn't.

The reviewer can be the same model as the implementer, the same model as the orchestrator, or a different one.
What matters is that it's a clean session. A different model may catch different things, so mixing is a bonus.

The reviewer is also **read-only**: it reports problems and doesn't fix them. If it fixes things, it becomes a second
builder and nobody is independently checking the result.

## What the reviewer checks

In order:

1. **Definition of done, mechanically:**
   - every check passes (the reviewer runs them);
   - only allowed files changed;
   - no tests were deleted, weakened, or skipped;
   - the working tree is clean;
   - the commit message matches the spec.
2. **Does it meet the spec,** including edge cases the spec implies?
3. **Test quality:** for each key test, would it really notice if the behavior broke? Compare it with the spec's "fails if" line,
   and look for tests that assert too little.
4. **Spec concerns:** does the spec itself look right? If the requirement or its assumptions look wrong or incomplete,
   the reviewer flags that separately and doesn't rewrite the requirement.
5. **Defects:** logic errors, unhandled input, leftover debug code, hardcoded values.
6. **Scope:** anything added that wasn't asked for.

## Reading the tests critically

The most useful test review needs no code changes. Take each key test and the spec's "fails if" line, and ask: *would this test
really fail if that happened?* In the worked example, the spec said the test should fail if the code changed a stack before
raising an error, but the test only checked that an error was raised. Reading the two side by side exposes the gap.

No review proves a test suite is comprehensive. Treat this as a way to catch hollow tests, not as proof the code is correct.

## The review prompt

> You are the reviewer. Read AGENTS.md. Here is the spec and here is the result. Do not read any report from
> the implementer. Your job is to find problems, not to approve. Run the checks yourself, and for each key test say whether it would really notice if the behavior broke. Flag anything in the spec that looks wrong.
> Write your findings to docs/reviews/REVIEW-003.md in the standard format.

The full template is in `templates/review.md`.

## Acting on the findings

The reviewer's output goes to the orchestrator, who decides:

- **Accept** if it passes.
- **Send back** with the specific fixes, in a fresh implementer session.
- **Rewrite the spec** if the failure is really an ambiguity in the spec.
- **Revisit the requirement** if the reviewer flagged a spec concern. That's a decision for you or the orchestrator.

Reviews that find nothing should say what was tried. Only the orchestrator (or you) merges, and only after a review passes: one owner integrates. "Looks good" isn't a review.

## Do this

Run a reviewer on your first completed task. Without reading it first, predict whether it will find problems.
Then compare. Whichever way it goes, you've learned something about your specs.

**Next:** [Chapter 10: Handling failures](10-handling-failures.md)
