# REVIEW-003: Stack limits

(The reviewer received the spec and the repository. It did not receive the implementer's report.)

## Definition of done
- [x] `./check` passes (ran it: 14 tests, lint clean)
- [x] Only allowed files changed
- [x] No tests deleted, weakened, or skipped
- [x] Working tree clean
- [x] Commit message matches the spec

## Meets the spec
Overflow splitting works. The full-inventory case raises the right error.

## Test quality (sanity-break check)
Ran the check on both key tests, using the spec's "fails if" lines.
- `test_overflow_splits_stack`: changing the limit to 100 makes it fail, as it should.
- `test_full_inventory_raises`: the spec says it should fail if the code changes a stack before raising the error.
  Reading the code, it already does exactly that (see Defects), and the test passes anyway. The test only asserts that
  the error is raised. It never checks that `stacks` is unchanged, so it can't notice this kind of failure.
Code left as found; working tree clean.

## Defects
In `Inventory.add`, the existing stack is filled to 99 *before* the free-slot check. When there's no room
for the remainder, the error is raised but the existing stack has already been topped up.
Reproduction: slots=1, one stack of (sword, 60); `add(sword, 50)` raises InventoryFullError and leaves the stack at 99.
The spec requires the inventory to be left exactly as it was.

## Scope
Nothing extra added.

## Result
VERDICT: FAIL
BLOCKING:
  1. src/inventory.py, `add`: mutates the existing stack before checking capacity. Must check first or roll back.
  2. tests/test_stack_limits.py, `test_full_inventory_raises`: does not assert that `stacks` is unchanged.
NOTES: none
CHECKS RUN: ./check; manual reproduction of the overflow case; sanity-break check on both key tests
