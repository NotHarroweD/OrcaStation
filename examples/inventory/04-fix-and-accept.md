# Fix and accept

## The orchestrator's decision
The failure traces to the implementation, not the spec: the spec already demanded "leave the inventory exactly as it was"
and named a test for it. So no spec rewrite. Send it back with the exact failures.

## Fix prompt (fresh implementer session; no history from attempt 1)

> You are the implementer. Read AGENTS.md and docs/specs/SPEC-003.md. This is fix round 2 on branch
> spec-003-stack-limits. A review found two problems with an earlier attempt:
> 1. `Inventory.add` fills the existing stack before checking whether the remainder fits. If it doesn't fit,
>    the error is raised but the stack has already changed. Check capacity first (or roll back).
> 2. `test_full_inventory_raises` must also assert that `stacks` equals its value from before the call.
> Fix both, commit as `fix: SPEC-003 review round 2`, and save your report to docs/reports/REPORT-003-2.md.

## Second implementer report (excerpt, from `REPORT-003-2.md`)

```
STATUS: COMPLETE
SUMMARY: add now checks capacity before changing any stack. test_full_inventory_raises also asserts `stacks` is unchanged.
COMMITS: fix: SPEC-003 review round 2
RED: test_full_inventory_raises failed against the old code (the stack had been topped up to 99)
GREEN: 2 passed
CHECKS: ./check passed (14 tests, lint clean)
```

The strengthened test failed against the old code, which is good evidence it now notices the problem.

## Second review (`REVIEW-003-2.md`)
VERDICT: PASS. The reviewer reproduced the earlier overflow case (the stack stays at 60) and confirmed that
`test_full_inventory_raises` now checks `stacks`, so it would notice a stack being changed before the error.
The orchestrator merged the branch.

## The record
Added to `docs/decisions.md`:

> - `Inventory.add` is all-or-nothing: if it can't place everything, it changes nothing.

Added to the orchestrator's notes for future specs: *when a spec says "change nothing on failure," name the test
that checks it and add a "fails if" line for it.*

## What this example shows
- Checks passing was not enough. The first attempt was wrong in a way no automated check noticed.
- The implementer's report looked convincing. The hollow test only showed up when the reviewer read the tests against the spec.
- The fix was cheap: a fresh session, two numbered problems, no rewrite.
- The lesson went back into the project's files, so future specs improve.
