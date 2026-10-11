# Fix and accept

## The orchestrator's decision
The failure traces to the implementation, not the spec: the spec already demanded "leave the inventory exactly as it was"
and named a test for it. So no spec rewrite. Send it back with the exact failures.

## Fix prompt (fresh implementer session; no history from attempt 1)

> You are the implementer. Read AGENTS.md and docs/specs/SPEC-003.md.
> A review found two problems with an earlier attempt:
> 1. `Inventory.add` fills the existing stack before checking whether the remainder fits. If it doesn't fit,
>    the error is raised but the stack has already changed. Check capacity first (or roll back).
> 2. `test_full_inventory_raises` must also assert that `stacks` equals its value from before the call.
> Fix both and report in the standard format.

## Second implementer report (excerpt)

```
STATUS: COMPLETE
SUMMARY: add now checks capacity before changing any stack. test_full_inventory_raises also asserts `stacks` is unchanged.
RED: test_full_inventory_raises failed against the old code (the stack had been topped up to 99)
GREEN: 2 passed
CHECKS: ./check passed (14 tests, lint clean)
```

The strengthened test failed against the old code, which is good evidence it now notices the problem.

## Second review
VERDICT: PASS. The reviewer reproduced the earlier overflow case (the stack stays at 60), re-ran the sanity-break check
on `test_full_inventory_raises` (changing a stack before raising now makes it fail), and confirmed the code was restored.

## The record
Added to `docs/decisions.md`:

> - `Inventory.add` is all-or-nothing: if it can't place everything, it changes nothing.

Added to the orchestrator's notes for future specs: *when a spec says "change nothing on failure," name the test
that checks it and add a "fails if" line for it.*

## What this example shows
- Checks passing was not enough. The first attempt was wrong in a way no automated check noticed.
- The implementer's report looked convincing. The hollow test only showed up when the reviewer ran a sanity-break check.
- The fix was cheap: a fresh session, two numbered problems, no rewrite.
- The lesson went back into the project's files, so future specs improve.
