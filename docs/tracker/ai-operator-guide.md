# AI Operator Guide

This is the no-nonsense guide for any future AI assistant working inside this ecosystem.

Read this before acting like the system is cleaner, more current, or more automated than it really is.

## Mission

Your job is not to admire the tracker.

Your job is to:

- identify where work honestly belongs
- keep the active trackers truthful
- avoid waking up legacy noise
- help the user ship real work through the system

## The System Split

Treat this split as law unless the user explicitly changes it.

### `BrynosRepo`

Use for:

- primary delivery work
- real active repos that should look like products or sustained tools

Current linked repos:

- `BrynosRepo/.github`
- `BrynosRepo/github-native-tracker-starter`
- `BrynosRepo/Personal-scripts`
- `BrynosRepo/Personal-dynamiccsar-missions`

### `bryant112`

Use for:

- incubators
- experiments
- account tooling
- early-stage product exploration

Current linked repos:

- `bryant112/.github`
- `bryant112/chsarp-dev-overview`
- `bryant112/LANDSPY`
- `bryant112/theLab-POC`
- `bryant112/madSci`
- `bryant112/StateBridge`
- `bryant112/feature-branch-test-brief`

## What To Trust

Highest trust:

- owner `.github` repos
- `docs/tracker/*.md`
- current project field lists
- current linked repo lists
- current issue inventory

Medium trust:

- repo README files
- current branch and working-tree status

Low trust:

- old repo descriptions
- legacy personal repo defaults
- any assumption that a repo is active just because it is not archived
- any assumption that tracker automation is fully configured

## Hard Truths About The Current System

- `BrynosRepo` process is more mature than `BrynosRepo` delivery adoption.
- `bryant112` tracker is structurally correct but currently empty.
- Many personal repos are legacy noise.
- Some active repos still have blank descriptions.
- Several personal repos still use `master` or even a `codex/...` branch as the default branch.
- The environment is not fully portable between WSL and Windows.

Do not hide these facts.

## Preferred Local Shortcuts

When the task starts fuzzy, prefer the local guided workflows instead of improvising a long intake.

- `Guide Me` is the front door for common work types.
- `$prompt-pattern-coach` is the step-by-step prompt builder.

These are local environment accelerators, not canonical process documents.

Their durable documentation lives in `docs/tracker/codex-guided-workflows.md`.

## How To Start Any Session

1. Ask: is this delivery work or incubator/tooling work?
2. Pick the owner based on that answer.
3. Check whether the repo is already linked to the right tracker.
4. Check whether an issue already exists.
5. If not, create the smallest honest issue instead of working from memory.
6. Keep the issue and Project state truthful as work moves.

## How To Evaluate A Repo Fast

Use this order:

1. repo description
2. README
3. issue count
4. current tracker linkage
5. default branch
6. recent push date
7. local branch and working-tree state if a checkout exists

If a repo has:

- no description
- no README signal
- no issues
- no tracker usage

then treat it as low-confidence until proven otherwise.

## How To Decide Whether A Repo Belongs In A Tracker

Link it if:

- it is active now
- it belongs to the owner’s role
- the user is likely to work from it again soon

Unlink it if:

- it is archive-style
- it is legacy
- it is too noisy
- it blurs the owner boundary

Never bulk-link every repo under an owner just because the CLI makes it easy.

## Tracker Rules

The active taxonomy is:

- `type:bug`
- `type:feature`
- `type:chore`
- `type:spike`
- `needs:triage`
- `severity:s1`
- `severity:s2`
- `severity:s3`
- `status:blocked`
- `area:frontend`
- `area:backend`
- `area:infra`
- `area:data`
- `area:docs`
- `area:tooling`
- `area:cross-cutting`

Do not reintroduce generic GitHub labels into active-flow repos unless the user explicitly wants that reversal.

## Project Rules

Both active trackers should have:

- `Status`
- `Priority`
- `Effort`
- `Iteration`

Status model:

- `Backlog`
- `Ready`
- `In Progress`
- `Blocked`
- `In Review`
- `Done`

Use the project for status and priority.

Use labels for type and area.

## Known GitHub Quirks

These matter in practice.

### Default Files

- owner `.github` repo must be public for default issue/PR files to apply broadly
- if a repo has its own `.github/ISSUE_TEMPLATE/`, the owner defaults stop applying for issue templates there

### Project Copy

- copying a project preserves fields and views
- copying a project does not preserve auto-add workflows

### Auto-Add

- auto-add only affects future items that match after the workflow is enabled
- auto-add does not backfill old issues

### CLI Repo Argument Quirk

In this environment, when using `gh project link` or `unlink` with `--owner`, prefer:

```bash
--repo REPO
```

not:

```bash
--repo OWNER/REPO
```

## Environment Quirks

### WSL GitHub CLI

If `gh auth status` works but plain `gh` or `git push` fails, use the WSL wrapper path:

```text
/home/neand/.local/bin/gh
```

This is an environment issue, not a repo issue.

### .NET

Do not assume `.NET` is available on `PATH` in the current shell.

In this environment, `StateBridge` documentation is currently Windows-oriented and the local shell used during this analysis did not have `dotnet` available directly.

## Behavior Rules For Future AI Work

- Do not treat `BrynosRepo` and `bryant112` as interchangeable.
- Do not call a repo “active” just because it was recently migrated.
- Do not confuse tracker readiness with tracker adoption.
- Do not let process work crowd out actual product issues.
- Do not create fake milestones or performative backlog bulk.
- Do not soften repo hygiene problems when the user asked for truth.
- Do not overvalue placeholder repos.

## Where To Push The System Next

If you need to make the system better, prefer this order:

1. create or refine a real issue in an active repo
2. move real work through the tracker truthfully
3. clean repo hygiene on the linked set
4. archive, rename, or downgrade ambiguous leftovers
5. only then improve docs or scaffolding further

## Best Next Candidates

For real delivery usage:

- `BrynosRepo/Personal-scripts`

For real incubator usage:

- `bryant112/LANDSPY`
- `bryant112/madSci`

For serious architecture work:

- `bryant112/StateBridge`

## Final Reminder

This system is good enough to use.

It is not good enough yet to run on autopilot.

Treat the main risk as drift, not as lack of tooling.
