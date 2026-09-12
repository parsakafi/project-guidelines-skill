# Dependency Guidelines

## Keep dependency usage intentional

Before adding a dependency, ask:

- is this necessary?
- is there already an equivalent in the project?
- is the package actively maintained?
- does it fit the project's existing ecosystem?
- is the license acceptable?
- does it add unacceptable runtime or bundle cost?

Do not add a dependency casually or for a one-off convenience.

## Dependency hygiene

Check for:

- unused dependencies
- outdated dependencies
- vulnerable packages
- mismatched lockfile and package manifest
- package manager drift

Use the project's normal update and install workflow.

Do not switch package managers without a clear repository reason.

## Security and maintenance

Prefer packages that are:

- mature
- maintained
- broadly used in the ecosystem
- suitable for the project's runtime version

Review advisories and release notes before upgrading dependencies, especially for breaking changes.

Update packages deliberately, one change at a time when practical, so failures are easier to diagnose.
