# Git and Repository Workflow

## Before editing

Run or inspect the equivalent of:

```bash
git status
git branch --show-current
git log --oneline -5
```

Understand the current branch and working tree.

Never discard pre-existing uncommitted changes.

## Branching

Use a dedicated branch for each coherent feature, bug fix, or maintenance task.

Prefer repository conventions such as:

```text
feature/<name>
bugfix/<name>
hotfix/<name>
```

Do not make feature work directly on protected production branches.

## Focused changes

Keep each change logically coherent.

Do not mix:

- unrelated refactoring
- formatting-only changes
- dependency upgrades
- feature work
- unrelated bug fixes

If an unrelated issue is discovered, report it instead of silently expanding scope.

## Commits

Use clear imperative commit subjects.

Preferred:

```text
Add retry handling for API requests
```

Avoid:

```text
fixed stuff
updates
changes
```

The body should explain why when the reason is not obvious from the diff.

## Synchronization

Before integration, fetch the target branch and use the repository's established workflow.

When rebasing a feature branch, prefer:

```bash
git push --force-with-lease
```

over unconditional force-pushes.

Never rewrite protected/shared branch history.

## Pull request readiness

Verify:

- focused diff
- tests pass
- lint passes when configured
- typecheck passes when configured
- build passes when configured
- no secrets
- documentation updated where behavior changed
- final diff reviewed

## Dependency and generated files

Respect the project's package manager and lockfile.

Do not switch package managers casually.

Do not commit generated build output unless the repository intentionally tracks it.

## Dangerous operations

Require explicit authorization before destructive actions such as:

```bash
git reset --hard
git clean -fd
git push --force
```

Never use these to solve a problem caused by uncertainty about the working tree.
