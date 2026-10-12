# REVIEW-XXX: <short title>

You are the reviewer. You did not write this. Your job is to find problems, not to approve.
You have the spec and the actual result. Do not rely on any report from the implementer.

## Definition of done
- [ ] Every required check passes (run them yourself)
- [ ] Only allowed files changed
- [ ] No tests deleted, weakened, or skipped
- [ ] Working tree is clean
- [ ] Commit message matches the spec

## Meets the spec
<Does the result do what the spec asks, including implied edge cases?>

## Test quality
<For each key test: would it really notice if the behavior broke? Compare it with the spec's fails-if line.>

## Defects
<Logic errors, unhandled input, leftover debug code, hardcoded values.>

## Scope
<Anything added that the spec did not ask for.>

## Spec concerns
<Evidence that the requirement or its assumptions are wrong or incomplete, or "none". Flag it; don't rewrite it.>

## Result
VERDICT: PASS | PASS_WITH_NOTES | FAIL
BLOCKING: <issues that must be fixed, each with file and location>
NOTES: <non-blocking observations>
SPEC CONCERNS: <summary, or none>
CHECKS RUN: <what you ran and the results>
