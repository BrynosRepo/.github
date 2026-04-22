# Codex Guided Workflows

This is the durable note for the guided Codex intake flows currently installed in the local environment.

These are not repo-scoped features.

They are local operator tools that make it faster to start work cleanly.

## What Exists

Current local skills:

- `Guide Me`
- `prompt-pattern-coach`

Current install paths:

- `~/.codex/skills/guide-me`
- `~/.codex/skills/prompt-pattern-coach`

Validation status as of April 21, 2026:

- both skills passed `quick_validate.py`

## Purpose

These skills exist to reduce prompt friction and improve throughput.

They are meant to:

- reduce vague first turns
- route work into the right lane faster
- ask one question at a time instead of dumping a form
- catch missing repo, scope, preservation, and verification details early

## Guide Me

`Guide Me` is the front door.

Use it when the user has not yet framed the task clearly and would benefit from a short curated menu first.

Current intended menu:

1. Make or fix something in a repo
2. Review current changes like a dev manager
3. Analyze a repo or system
4. Set up or tune GitHub tracker or workflow
5. Write or tighten docs, playbooks, or guides
6. Refactor safely without changing behavior
7. Build the right Codex prompt
8. Something else

Behavior rule:

- after the menu, ask one short question at a time

## Prompt Pattern Coach

`$prompt-pattern-coach` is the prompt-builder lane.

Use it when the job is to create a strong Codex prompt rather than immediately execute work.

Current supported patterns:

- direct implementation
- focused review
- safe refactor
- repo triage
- tracker-aware work

Behavior rule:

- choose the right pattern, then fill it question by question

## Relationship To Canonical Docs

The skills themselves live locally.

The durable memory for how and why they exist lives here in the owner `.github` docs, because that is the reusable system memory across sessions and devices.

Related canonical docs:

- `docs/tracker/codex-throughput-guide.md`
- `docs/tracker/ai-operator-guide.md`

## When This Does And Does Not Belong In Project Tracking

Do not create a project item just because a local skill prompt was tuned.

Local workflow tuning usually does not belong in the active delivery tracker.

Create a project item only if one of these becomes true:

- the skill is being packaged or shared for team use
- the skill needs to be versioned in a repo instead of staying local
- the guided workflow changes require canonical doc updates across owners
- the work becomes part of real delivery enablement instead of private local ergonomics

That keeps the trackers focused on delivery and real operating-system work rather than every small local assistant tweak.

## Maintenance Rules

- keep the menu short and stable
- prefer lanes that match real repeated work
- ask one question at a time
- stop once the next prompt or work brief is obvious
- keep pitfalls explicit
- if the work pattern changes, update this doc and the local skill together
