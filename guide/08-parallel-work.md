# Chapter 8: Parallel work

**In one line:** run independent tasks at the same time, but only after you've made sure they can't collide.

## When it's safe

Two tasks are candidates for parallel work when their dependencies are done, their interfaces are agreed, and each can be built
and tested independently. Giving each task exclusive ownership of its files helps prevent collisions, but different files don't
guarantee independent work (see below).

Check that:

1. Neither depends on the other's output.
2. They don't share state, or an interface that isn't settled yet.
3. Each can be tested on its own.
4. They touch **different files**, so they can't collide.

```mermaid
flowchart TD
    T11["T1.1 Data types"] --> T12["T1.2 Add / remove"]
    T12 --> T13["T1.3 Stack limits"]
    T12 --> T14["T1.4 Weight limits"]
    T13 --> T21["T2.1 Save"]
    T14 --> T21
```

Here T1.3 and T1.4 can run side by side. T2.1 has to wait for both.

## Rules that prevent collisions

1. **Define shared interfaces first.** If two tasks must agree on a function signature or data shape,
   write that down in a spec that finishes before either starts, or quote it in both specs.
2. **Exclusive file ownership.** Each parallel task lists its allowed files, and no file appears in two of them.
   If two tasks need the same file, they're not parallel.
3. **Separate branches or working copies.** Each implementer works on its own branch, ideally in its own folder.
   Git worktrees are a convenient way to do this: each one checks out a different branch into its own folder,
   so half-finished work never mixes.
4. **Merge in dependency order,** one at a time, running the checks after each merge.

## File ownership is a shortcut, not the goal

Exclusive file ownership is a stand-in for the real goal: tasks that can't interfere with each other.
Two tasks can touch different files and still be tightly coupled. Before running tasks in parallel, ask:

1. Do they share state?
2. Do they share an interface?
3. Does one rely on the other's behavior?
4. Can each be tested on its own?
5. Can each be merged on its own?

If any answer is yes, run them in sequence, or define the shared piece first. Wait for every task in a batch to finish
and pass review before integrating, and let one owner (the orchestrator, or you) do the merging.

## Avoiding deadlock

Deadlock here means tasks waiting on each other forever.

- **No circular dependencies.** If A waits for B and B waits for A, you've cut the tasks wrong. Redraw them.
- **No waiting inside a task.** An implementer should never wait for another session. If it needs something
  that isn't there, it reports NEED_INFO and stops.
- **Dependencies live in the plan,** not in the implementers' heads.

## The integration task

After parallel tasks merge, add a short integration task whose only job is to confirm the pieces work together
(a few tests that use both features). Parallel work trades some integration risk for speed, and this task covers it.

## How many at once?

Fewer than you think. Parallel sessions multiply your review load, since every result needs a reviewer.
Two or three at a time is plenty for most projects. More only helps if review keeps up.

## Do this

Look at your plan and mark which tasks could run in parallel. For each pair, verify they share no files.
If they do, either split the shared file or run them in sequence.

**Next:** [Chapter 9: Adversarial review](09-adversarial-review.md)
