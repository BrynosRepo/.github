# Current Baseline

Last updated: April 21, 2026

This file is the durable memory note for the current `BrynosRepo` tracker baseline.

## Role

`BrynosRepo` is the primary delivery owner.

Its `Delivery Tracker` project is the place for active delivery work, not for every repo under the org.

## Defaults Repo

- `BrynosRepo/.github` is public
- it is the owner-wide source of default issue forms, PR template, and tracker docs

## Project

- project name: `Delivery Tracker`
- owner: `BrynosRepo`
- visibility: private
- project number: `1`
- field count: `13`

Planning fields in use:

- `Status`
- `Priority`
- `Effort`
- `Iteration`

## Linked Repos

As of this baseline, the project is intentionally linked only to:

- `BrynosRepo/.github`
- `BrynosRepo/github-native-tracker-starter`
- `BrynosRepo/Personal-scripts`
- `BrynosRepo/Personal-dynamiccsar-missions`

Repos intentionally left unlinked:

- archive-style repos
- low-signal repos that would dilute the main delivery view

## Label Policy

Active-flow repos in this owner should use only the lean tracker taxonomy:

- `type:*`
- `area:*`
- `severity:*`
- `needs:triage`
- `status:blocked`

Generic GitHub labels were pruned from the active-flow repos during this rollout after checking that live issues were already using the lean taxonomy.

## Manual Or UI-Only Follow-Ups

These still matter after the CLI/bootstrap pass:

- confirm or duplicate `Auto-add to project` workflows in the GitHub Project UI
- keep the `Item added` -> `Backlog` workflow enabled
- keep the `Item closed` -> `Done` workflow enabled
- keep the `Pull request merged` -> `Done` workflow enabled

Remember:

- auto-add does not backfill old matching issues
- copied projects do not bring auto-add workflows with them

## Operational Notes

- use `github-native-tracker-starter` as the reference repo when validating or teaching the workflow
- use `Personal-scripts` as the first live non-starter delivery repo when dogfooding the tracker flow
- keep this owner focused on real delivery work; move incubators and account-tooling repos elsewhere
