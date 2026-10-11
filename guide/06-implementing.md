# Chapter 6: Implementing

**In one line:** the implementer's job is to follow the spec exactly, watch its tests fail before it builds, and report honestly.

## Starting the session

Open a fresh session on a cheaper tier and give it three things: its role, `AGENTS.md`, and one spec.

> You are the implementer. Read AGENTS.md, then docs/specs/SPEC-003.md. Do exactly what it says.

Nothing else. No extra context, no conversation history. The spec is the whole job.

## The sequence

1. **Read the whole spec** before touching anything.
2. **Write the tests first** and run them. They should fail, and for the right reason.
3. **Implement** until they pass.
4. **Run every check** the spec lists.
5. **Commit** only the allowed files, with the exact message from the spec.
6. **Report:** save it to `docs/reports/REPORT-<id>.md` in the fixed format from `AGENTS.md`, commit it separately,
   and paste the same text as the final message. The orchestrator reads the file, not the chat.

## Why tests first

A test that can't fail proves nothing, and cheaper models sometimes write tests that pass no matter what.
Watching a test fail before the code exists is a basic guard: it shows the test notices a missing feature.

A stronger check, the **sanity-break check**, belongs to the **reviewer**, not the implementer (Chapter 8).
Keeping it with the reviewer means the builder isn't marking its own homework, and it keeps this chapter simple.

## When the implementer should stop

Stopping is a feature. The implementer should halt and report instead of pushing on when:

- the same failure survives three fix attempts;
- the spec contradicts the code;
- the spec is impossible as written;
- it needs something outside the allowed files.

A BLOCKED report with a clear reason is far cheaper than an hour of flailing.

## Choosing the tier

If you're new, start the implementer one step above the cheapest tier so you can tell spec problems from model problems,
then tune down. [Chapter 12](12-choosing-tiers.md) covers this in detail. Over time, you're looking for the lightest tier
that finishes reliably.

- If tasks pass on the first try, you may be able to go lighter still.
- If it fails repeatedly on well-written specs, move up one tier.
- If it fails on *poorly* written specs, fix the spec, not the tier.

Every model has a point where task size or complexity makes it start failing. Find yours by experiment
and keep specs under it.

## Don't continue long sessions

When a task is done, end the session. If a fix is needed, a fresh session with the exact failure is
usually better than extending a long one. Old context is exactly what you're trying to avoid.

## Do this

Run SPEC-001 through an implementer session. Read its report before looking at the code.
Did it follow the format? Did it report any deviations?

**Next:** [Chapter 7: Parallel work](07-parallel-work.md)
