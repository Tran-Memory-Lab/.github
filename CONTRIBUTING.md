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
- New Project boards start from the organization template **`Tran Memory Lab Work Template`**.
  It uses one Status lifecycle (`Triage → Backlog → Ready → In Progress → In Review → Done`),
  `Area` for VR work, `Component` for scientific-pipeline work, `Priority`, `Rig Verification`,
  and `Due Date`. There is no separate headset column.
- An issue form can add an issue to a board, but it cannot set the board's fields. Set `Area` or
  `Component`, `Priority`, and `Rig Verification` on the card yourself.

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

**Headset-required issues** (`Rig Verification: Needs Headset Check`):

1. Write `Refs #N` in the pull request description, **not** `Closes #N`, `Fixes #N`, or
   `Resolves #N`. A closing keyword closes the issue on merge and moves it to `Done`.
2. After merge the issue stays open in `In Review` with `Needs Headset Check`.
3. Only after someone checks the behaviour in the headset and records the evidence on the issue
   does a person set `Rig Verification: Verified on Rig`, close the issue, and move it to `Done`.

**Code-only issues** may use `Closes #N` and reach `Done` after review and merge.

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
