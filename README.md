# Project Guidelines Skill

This repository contains a reusable agent skill for applying practical engineering standards to JavaScript and Node.js work.

## Purpose

The skill helps a code agent:

- inspect a repository before making changes
- follow existing conventions when they are reasonable
- keep changes small and scoped
- validate with the project's own checks
- review output for security, accessibility, and quality issues

## Structure

- `SKILL.md` — main skill definition and guidance
- `ORIGIN.md` — attribution and source context
- `references/` — task-specific guidance files
  - `git.md`
  - `documentation.md`
  - `environments.md`
  - `dependencies.md`
  - `javascript.md`
  - `testing.md`
  - `code-style.md`
  - `logging.md`
  - `rest-api.md`
  - `security.md`
  - `accessibility.md`

## Instructions for Use

Install the skill from the command line:

```bash
npx skills install parsakafi/project-guidelines-skill
```

Or place this directory in a skills-compatible location manually, such as:

- `.github/skills/project-guidelines`
- `.agents/skills/project-guidelines`
- `.claude/skills/project-guidelines`

Then:

1. Ensure the folder contains the `SKILL.md` file at the root of the skill directory.
2. When a task matches the skill's scope, load the relevant references before implementing.
3. Use the guidance to inspect the repo, plan a minimal change, implement carefully, and validate with the project's own tooling.
4. Keep the final output focused on the user request and avoid unrelated refactors.

## Reference Selection

Use only the references relevant to the task:

- Git and repository workflow: `references/git.md`
- Documentation: `references/documentation.md`
- Environments and configuration: `references/environments.md`
- Dependency management: `references/dependencies.md`
- JavaScript and Node.js implementation: `references/javascript.md`
- Testing and validation: `references/testing.md`
- Code style: `references/code-style.md`
- Logging: `references/logging.md`
- REST API work: `references/rest-api.md`
- Security-sensitive work: `references/security.md`
- Accessibility and browser UX: `references/accessibility.md`

## Source Reference

This skill is adapted from the project-guidelines repository:

- https://github.com/elsewhencode/project-guidelines

The upstream project contains the broader engineering guidance that this skill distills into a reusable agent-focused format. See also [ORIGIN.md](ORIGIN.md) for provenance and attribution details.

## Notes

This skill is intended to be a practical default, not a mandate to modernize or rewrite an existing project. Existing repository conventions should take precedence unless a requirement or engineering problem clearly justifies a change.
