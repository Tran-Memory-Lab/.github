# Contributing to Tran Memory Lab repositories

These are organization-wide defaults. A repository's own `CONTRIBUTING.md`, `AGENTS.md`, or
`.github/` files always take precedence over this one.

## What these defaults do and do not do

GitHub uses a file from this `.github` repository **only when a repository has no file of the
same kind of its own**. Nothing here is copied into, merged with, or enforced on other repositories.

- **Issue forms** here (`task.yml`, `bug.yml`, `spike.yml`) appear only in repositories with no
  `.github/ISSUE_TEMPLATE/` folder. `object-location` has its own (`olm_task.yml`, `olm_bug.yml`),
  so these do not appear there.
- **The pull request template** here appears only in repositories with no PR template of their
  own. `object-location`, `template-data-pipeline`, and `template-vr-experiment` each have one,
  so this template does not apply there.
- **Labels are not inherited** from this repository. Each repository has its own labels.
- **Workflows are not inherited.** Versioned reusable workflows, validators, and the raw-data
  hook live in `Tran-Memory-Lab/lab-repo-kit`, and each repository calls them at a pinned tag.

## Where work is tracked

- **Commit razor:** if closing an item needs a commit to a repository, it is a GitHub issue on
  that repository's Project board. If it does not (IRB, scheduling, protocol wording, writing), it
  is tracked outside GitHub. Never track the same item in both places.
- **Each repository's `docs/agents/TRACKING.md`** defines its board: the fields, their options,
  which ones you set by hand, and how issues are filed and closed. Read it before filing or moving
  an issue. Field names differ between repositories, so this file does not list them.
- New boards are copied from the organization template **`Tran Memory Lab Work Template`** by the
  lab's tracking setup, which also writes that repository's `TRACKING.md`.

## Writing an issue

Every form follows the same shape, so a card can be read in a few seconds and an agent taking an
item knows its limits as well as its goal:

- **Summary & High-Level Plan** comes first: one to three sentences, the exact problem or
  requirement, then the mechanism that solves it.
- **Out of Scope** names what must not be touched, for people and agents alike.
- **Done When** is a list of checkboxes that each answer yes or no. Name the test, file, or
  number that shows it.
- **Agent Contract** is filled in only when an AI agent may take the item: write scope,
  non-goals, and the command that verifies it.

Use **Task** for work that needs a commit, **Bug report** for behaviour that is wrong, and
**Spike** for a time-boxed question that must be answered before production work starts. The pull
request template mirrors the issue: the author ticks the issue's own criteria.

## Merge is not verification

A merged pull request shows that code was reviewed and integrated. It never shows that the
behaviour was checked on the physical VR rig, and it never shows that a scientific result is valid.

Work that only a person can check (in a headset, a browser, on a rig) stays open after merge:

1. Its pull request references the issue without a closing keyword (`Refs #N`, not `Closes #N`,
   `Fixes #N`, or `Resolves #N`). A closing keyword closes the issue on merge.
2. The issue stays open until someone checks the behaviour and records the evidence on it.
3. Only then does a person mark it verified, close it, and move it to `Done`.

The field that marks this work, and its option names, are in the repository's
`docs/agents/TRACKING.md`. Code-only issues may use `Closes #N` and reach `Done` after review and merge.

## Data boundary

No repository may contain raw participant data, raw gaze or eye-tracking logs, raw exports,
participant identifiers, or uncurated video or audio. Commit only synthetic fixtures,
de-identified toy datasets, schemas, and test manifests. Raw materials stay in approved
institutional storage.

The `lab-repo-kit` raw-data hook and CI check catch common mistakes by path, extension, size, and
known participant columns. They are guardrails, not proof: renamed files and data inside archives
can slip past them. On GitHub Free, CI checks on private repositories report failures but cannot
block a merge, so reviewers must look.

## Branches and commits

Work on a branch, open a pull request, and get review before merging to `main`. Follow the
repository's own branch and push rules where it has them.
