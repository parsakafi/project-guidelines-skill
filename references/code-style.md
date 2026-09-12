# Code Style Guidelines

## Follow the repository standard

Use the project's established linting, formatting, and editor configuration.

Common tools include:

- ESLint
- Prettier
- editorconfig
- lint-staged
- husky

Do not introduce another formatter or lint tool if the repository already has one that works.

## Code quality

Prefer code that is:

- readable
- consistent
- small and focused
- easy to test
- easy to review

Use modern JavaScript syntax only when it aligns with the repository's existing baseline and compatibility requirements.

## Naming and structure

Use descriptive names that communicate intent.

Prefer:

- function names as verbs or verb phrases
- clear module boundaries
- a step-down structure where higher-level logic appears before lower-level helpers

Avoid vague names and unrelated naming churn.

## Review and cleanup

Remove:

- stale comments
- commented-out code
- temporary debug statements
- disabled lint rules that no longer need to be suppressed

If a temporary TODO is retained, make sure it is specific and actionable.
