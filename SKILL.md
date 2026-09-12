---
name: project-guidelines
description: Apply maintainable JavaScript and Node.js engineering practices during implementation, refactoring, debugging, code review, testing, API work, and release preparation. Use this skill when a task involves project structure, Git workflow, JavaScript quality, tests, REST APIs, security, or web accessibility.
license: MIT
---

# Project Guidelines

Use this skill as a practical engineering standard for JavaScript and Node.js projects.

## Instructions for use

This skill is designed to guide an AI coding agent during implementation, debugging, refactoring, testing, API work, and release checks in a repository.

Use it when the task involves:

- project structure or repo conventions
- Git and branch hygiene
- JavaScript or Node.js implementation work
- tests, linting, build validation, or type checks
- REST API or integration changes
- security-sensitive code paths
- browser or accessibility work

Standard workflow:

1. Inspect the repository before editing anything.
2. Read only the relevant reference files for the task.
3. Keep the change narrow and aligned with existing project conventions.
4. Add or update tests for behavior changes when practical.
5. Run the repository's existing validation commands before finishing.
6. Review the final diff for unintended or risky edits.

Use the reference files as the task-specific guidance layer, not as a broad rewrite mandate.

The skill is intentionally modular. Read only the reference files relevant to the current task.

## Core behavior

1. Inspect the repository before changing it.
2. Follow existing project conventions unless they conflict with an explicit requirement or create a clear engineering/security problem.
3. Keep changes focused and minimal.
4. Do not rewrite unrelated code.
5. Do not introduce dependencies, frameworks, tooling, or architectural migrations without a concrete reason.
6. Treat external input as untrusted.
7. Add or update tests for behavior changes when practical.
8. Run the repository's existing validation commands before finishing.
9. Review the final diff for accidental changes, secrets, debug code, dead code, and missing documentation.
10. Never destroy or overwrite user changes without explicit authorization.

## Task routing

Load the appropriate references before implementation or review:

- Git/repository workflow: `references/git.md`
- Documentation: `references/documentation.md`
- Environments/configuration: `references/environments.md`
- Dependency management: `references/dependencies.md`
- JavaScript/Node.js implementation: `references/javascript.md`
- Testing and validation: `references/testing.md`
- Code style and formatting: `references/code-style.md`
- Logging: `references/logging.md`
- REST/API work: `references/rest-api.md`
- Security-sensitive work: `references/security.md`
- Browser/UI/accessibility work: `references/accessibility.md`

For tasks spanning multiple areas, load all applicable references.

## Standard workflow

### 1. Inspect

Determine:

- package manager and lockfile
- runtime/version configuration
- package scripts
- module system
- lint/format configuration
- type-checking configuration
- test framework
- build system
- application structure
- relevant tests
- repository status

Do not assume commands exist. Inspect `package.json` and project documentation first.

### 2. Plan

Before substantial changes, identify:

- files to modify/create
- behavior being changed
- tests required
- documentation affected
- compatibility concerns
- security implications
- migration requirements, if any

Prefer the smallest implementation that satisfies the requirement.

### 3. Implement

During implementation:

- preserve established conventions
- keep modules focused
- avoid unrelated refactors
- avoid unnecessary dependencies
- validate external input
- preserve compatibility unless a breaking change is intentional
- keep side effects explicit
- avoid hard-coded secrets and environment-specific values

### 4. Validate

Use the project's own scripts where available. Typical checks are:

```bash
npm test
npm run lint
npm run typecheck
npm run build
```

Do not invent scripts. Run only commands supported by the repository.

If a validation step fails:

1. determine whether the change caused it;
2. inspect the failure;
3. fix the underlying problem;
4. rerun the relevant check.

### 5. Review

Before completing the task:

```bash
git diff
git status
```

Check for:

- unintended changes
- secrets or credentials
- debug logging
- commented-out production code
- dead code
- unnecessary dependencies
- missing tests
- missing docs
- security regressions
- accessibility regressions
- formatting/type errors

### 6. Report

Summarize:

- what changed
- tests/checks run
- important design decisions
- known limitations or follow-ups

Clearly distinguish completed work from recommendations.

## Project precedence

These are defaults, not a mandate to refactor an existing project into a different style.

Existing repository conventions take precedence for:

- directory layout
- package manager
- module system
- formatter
- linter
- test framework
- API conventions
- naming
- CI commands

Do not perform broad modernization merely to satisfy this skill.

## Non-goals

Do not:

- upgrade dependencies without reason
- introduce Docker solely for convention
- introduce TypeScript solely because it is preferred
- replace working tooling without a concrete benefit
- change public API contracts without authorization
- rewrite unrelated files
- remove user changes
- commit secrets
- use destructive Git commands without explicit authorization
