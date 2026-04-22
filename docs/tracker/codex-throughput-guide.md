# Codex Throughput Guide

This is the practical guide for developers who want to get more real work done with Codex instead of just having nicer chats with it.

Use this when the goal is throughput:

- faster issue-to-PR time
- less context switching
- fewer half-finished explorations
- tighter verification
- cleaner handoff between human and AI

## First Principle

Codex is best when you give it:

- a real repo
- a real objective
- a real constraint set
- a real definition of done

Codex is worst when you give it:

- a vague idea
- three unrelated goals at once
- no file or repo context
- no signal about whether you want analysis, implementation, or review

The fastest teams do not “prompt better” in the abstract.

They reduce ambiguity earlier.

## The Best Use Cases

Use Codex aggressively for:

- repo orientation
- issue-to-implementation work
- debugging with logs or failing tests
- test creation
- doc cleanup while code is fresh
- repetitive repo hygiene
- migration and refactor passes with clear boundaries
- pull request review and risk spotting

Use Codex more carefully for:

- architecture choices with real tradeoffs
- scope decisions across multiple repos
- anything touching unclear product intent

Use Codex lightly for:

- open-ended brainstorming with no target artifact
- “what should we build” conversations before anyone has decided what matters

## The Throughput Loop

This is the highest-yield pattern.

### 1. Frame The Work

Start with:

- repo name
- branch or issue if relevant
- exact outcome wanted
- constraints
- what counts as done

Good:

```text
In LANDSPY, add a CSV import validation step before save. Keep the current UI flow. Add tests. If anything is unclear, assume the current desktop-first behavior stays the same.
```

Weak:

```text
Help me improve imports.
```

### 2. Let Codex Build Context First

If the codebase is not already obvious, ask Codex to inspect before changing.

Good:

```text
Scan the current import flow in LANDSPY, find where validation belongs, then implement it.
```

This prevents “fast wrong” edits.

### 3. Keep The Task Single-Threaded

One turn should usually have one outcome:

- fix the bug
- add the feature
- review the PR
- document the system

Not:

- redesign the architecture
- clean CI
- rename repos
- rewrite docs
- fix three bugs

Batching unrelated work feels efficient. It usually lowers quality and increases retries.

### 4. Ask For Execution, Not Just Advice

If you want code changed, say so.

Good:

```text
Make the change.
```

Good:

```text
Implement this and verify it.
```

Weak:

```text
What would you do here?
```

That question is fine for strategy work, but it is slower when the real ask is implementation.

### 5. Require Verification

Always ask for at least one of:

- run the tests
- add tests
- validate the command path
- tell me what could not be verified

Throughput is not just speed. It is speed without silent breakage.

### 6. Close The Loop

Before ending the task, have Codex:

- summarize what changed
- call out risk
- note anything not verified
- update docs if the workflow changed

This keeps follow-up turns small.

## Prompt Patterns That Save Time

### Pattern 1: Direct Implementation

```text
In REPO, implement X. Preserve Y. Add or update tests. Tell me any assumptions after the work is done.
```

### Pattern 2: Focused Review

```text
Review the current changes like a dev manager. Prioritize bugs, regressions, missing tests, and risky assumptions.
```

### Pattern 3: Safe Refactor

```text
Refactor this module for readability without changing behavior. Keep the public API stable and run the relevant tests.
```

### Pattern 4: Repo Triage

```text
Do a concentrated system analysis of this repo: what is solid, what is weak, what is missing, and what should be fixed first.
```

### Pattern 5: Tracker-Aware Work

```text
Check whether this work already exists as an issue in the right tracker. If not, create the smallest honest issue, then implement the change.
```

## What To Hand Codex Up Front

The more this is present, the faster the result:

- issue link or issue number
- file paths
- screenshots or error text
- failing command
- desired behavior
- non-negotiable constraints
- whether you want code, review, or explanation

Best shortcut:

- give Codex the artifact, not the summary

Examples:

- paste the error
- point at the file
- point at the issue
- point at the PR

## Throughput Killers

These are the habits that waste the most time.

### Mixing Strategy And Execution In One Ask

Bad:

- “analyze the whole system, redesign it, fix bugs, write docs, and prep a roadmap”

Better:

1. analyze
2. choose direction
3. implement one slice

### Hiding The Real Goal

If the goal is “ship this fix today,” say that.

If the goal is “understand whether this repo is worth keeping,” say that.

Codex does better when the real success condition is explicit.

### Oversized First Turns

Do not start with the entire quarter.

Start with the next meaningful chunk.

Good chunk size:

- one repo
- one problem
- one feature slice
- one review target

### Treating Codex Like A Search Engine

Codex is strongest when it can inspect, modify, and verify in the actual workspace.

If you only ask generic questions, you leave most of the value on the table.

### Skipping Verification

The apparent fast path is:

- ask for change
- read summary
- move on

The real fast path is:

- ask for change
- run verification
- catch the issue now

## Common Pitfalls

These are the mistakes that make teams think Codex is underperforming when the real problem is workflow shape.

### Pitfall 1: Treating Confidence As Proof

Codex can sound certain while still operating on incomplete context.

Counter:

- require file inspection
- require command output
- require verification
- ask what assumptions were made

### Pitfall 2: Feeding It Stale Or Fake Context

If the README lies, the issue is vague, or the tracker is empty, Codex has less to anchor to.

Counter:

- keep docs honest
- create the issue first
- point Codex at the real source of truth

### Pitfall 3: Letting One Turn Span Too Much Surface Area

When one ask touches too many files, repos, or goals, quality usually drops and rework rises.

Counter:

- split discovery from execution when needed
- keep one meaningful outcome per turn
- break multi-repo work into clear slices

### Pitfall 4: Asking For Refactors Without Behavior Guards

“Clean this up” is dangerous if there is no stability constraint.

Counter:

- say what must not change
- ask for tests or targeted verification
- keep public APIs stable unless change is intended

### Pitfall 5: Forgetting To Mention A Dirty Worktree

Codex can work around unrelated changes, but only if it knows they exist and can inspect them carefully.

Counter:

- mention if the branch is already in progress
- mention if there are user changes not to disturb
- ask Codex to preserve unrelated work

### Pitfall 6: Using Codex To Avoid Decisions

Codex can accelerate execution, but it should not be used to dodge ownership on product or scope calls.

Counter:

- decide the owner
- decide the repo
- decide the goal
- then use Codex to move faster inside that lane

### Pitfall 7: Ending The Session Too Early

Many teams stop after “the code is changed” and skip the rest.

Counter:

- verify
- update docs if behavior changed
- note follow-up risk
- move the issue or tracker state

### Pitfall 8: Using It Only For Greenfield Work

Codex is often even more valuable on:

- cleanup
- migration
- tests
- documentation
- repo hygiene

If the team only uses Codex for shiny feature work, it misses a lot of easy throughput gains.

## Best Team Habits

Teams move fastest when they standardize a few behaviors.

### 1. Issue First For Non-Trivial Work

If work is going to take more than a quick edit, create the issue first.

That gives Codex:

- context
- expected scope
- a place to track assumptions

### 2. Keep Repo Docs Honest

Codex gets better when README, descriptions, and setup docs reflect reality.

Bad docs create bad context windows.

### 3. Use Canonical Memory

In this ecosystem, the durable memory lives in the `.github` docs.

For system-level work, start from:

- `docs/tracker/current-baseline.md`
- `docs/tracker/bootstrap-playbook.md`
- `docs/tracker/system-analysis-2026-04-21.md`
- `docs/tracker/ai-operator-guide.md`

Do not rely on vibes when the docs already exist.

### 4. Let Codex Finish The Boring Last 20 Percent

High-value closeout work:

- tests
- docs
- issue updates
- tracker status cleanup
- release notes
- README touchups

Humans often skip these because they are tired by then.

Codex is useful precisely there.

### 5. Keep Working Trees Understandable

Codex can work in dirty repos, but throughput is best when:

- the branch has a clear purpose
- unrelated edits are limited
- the repo state is not a mystery

## Manager Moves

If you are a lead or manager using Codex across a team, ask for:

- repo health snapshots
- PR risk reviews
- issue decomposition
- test gap analysis
- repetitive hygiene work
- environment setup docs to be normalized

Do not use Codex as a replacement for product priority decisions.

Use it to compress execution and reduce drag around those decisions.

## My Blunt Tips

These are the highest ROI habits.

- Ask for the change you actually want, not the conversation you think should come first.
- Point Codex at the real repo and real files as early as possible.
- Prefer “implement and verify” over “what are some ideas.”
- One strong turn beats five fuzzy turns.
- Make Codex write the docs while the code context is still hot.
- Use Codex to kill backlog sludge, not just to generate new work.
- If a repo is ambiguous, ask for a system readout before asking for changes.
- If the work spans multiple repos, decide the owner boundary first.
- If you want speed, reduce ambiguity. If you want quality, require verification. If you want both, do both.

## Recommended Operating Pattern For This Ecosystem

For `BrynosRepo` and `bryant112`, the best pattern is:

1. identify the right owner
2. check whether the repo belongs in the active tracker
3. confirm whether the issue already exists
4. create or refine the issue if needed
5. ask Codex to implement against that scope
6. have Codex verify
7. update docs and tracker state before ending

That pattern is not fancy.

It is just reliable.

## Final Rule

The point of Codex is not to feel productive.

The point is to move real work with less drag.

If a prompt does not help Codex:

- find the right context faster
- change the right thing
- verify the result
- leave the system clearer

then the prompt probably needs tightening.
