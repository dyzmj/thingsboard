---
name: merge-release-branches
description: Workflow command scaffold for merge-release-branches in thingsboard.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /merge-release-branches

Use this workflow when working on **merge-release-branches** in `thingsboard`.

## Goal

Synchronizes changes between release branches (e.g., merging lts-4.2 into lts-4.3, rc into master) to keep branches up to date.

## Common Files

- `pom.xml`
- `application/pom.xml`
- `build.sh`
- `edqs/pom.xml`
- `monitoring/pom.xml`
- `msa/*/pom.xml`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Create a merge commit from source branch into target branch.
- Resolve any conflicts if necessary.
- Update common build files (e.g., pom.xml, build.sh, gradle files) and documentation if affected.
- Push the merge commit.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.