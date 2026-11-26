# Changelog

## v1.0.0 (first public release)

The first public release of the guide, playbooks, agent instructions, templates, and worked example.

Changes since the tester draft:

- **Fix rounds are now defined.** One work commit per attempt: the spec's exact message first, then
  `fix: SPEC-XXX review round N`. Later rounds save `REPORT-XXX-N.md` and `REVIEW-XXX-N.md`.
- **Reviewers don't see the implementer's report.** The report is committed on the branch under review, so the
  reviewer is told not to open `docs/reports/` and to leave it out of the diff.
- **Phase 0 is set up by hand.** The skeleton (repo, `check`, one passing test) is part of setup and needs no spec.
  Spec numbering starts at Phase 1, and `plan.md` records which spec covers which task.
- **The Chapter 5 spec matches the worked example,** and both close the "more than 99 at once" gap.
- **Help for chat-app users** in the Lite playbook: you run the commands and paste the output, and the reviewer
  gets output you captured yourself.
- **Notes on `check` for Windows, engines, and cloud agents** in Chapters 2 and 3.
- **The model reference was re-verified** and now maps each vendor's lineup to the three tiers.
- Smaller fixes for consistency across the cheat sheet, session starters, review template, and README.
