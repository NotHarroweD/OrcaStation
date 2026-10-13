# SPEC-XXX: <short title>

## Why
<One or two sentences on the purpose.>

## Allowed files
- <path/to/file>
- <path/to/test_file>

## Task
<Exactly what to build. Close every ambiguity: names, behavior, error cases.>

## Facts
- <Constants, signatures, and existing code to use, quoted rather than described.>
- <Relevant lines from docs/decisions.md.>

## Verification
Use automated tests wherever the behavior can be tested automatically. For anything else, name the explicit check instead.

**Automated tests (write first; they must fail before you implement)**
- <Behavior to test>
  - fails if: <a change to the code that this test should catch>
- <Behavior to test>
  - fails if: <a change to the code that this test should catch>

**Other acceptance checks (for what tests can't cover: visuals, feel, documentation, and so on)**
- [ ] <A specific, checkable criterion, and who or what checks it>
- [ ] <Another criterion>

**Not verifiable here:** <Anything this spec can't verify, so the reviewer and owner know, or "none".>

A manual check confirms the task once. It doesn't protect against future breakage the way an automated test does.

## Checks
<The exact command(s), e.g. ./check>

## Commit
<exact commit message>

## Report
Save to docs/reports/REPORT-XXX.md in the standard format, and commit it separately.

## Out of scope
<What not to do.>
