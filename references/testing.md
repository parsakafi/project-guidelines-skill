# Testing and Validation

## General rule

Behavior changes should have automated tests whenever practical.

Do not rewrite the project's entire testing strategy for a single feature.

Use the existing framework and conventions.

## Before implementation

Inspect:

- test scripts in `package.json`
- test framework configuration
- existing test naming
- fixture/factory conventions
- unit/integration/e2e boundaries
- CI test commands

## Test design

Prefer code that is:

- deterministic
- isolated
- explicit about dependencies
- easy to set up and tear down

Separate business logic from:

- network calls
- filesystem access
- current time
- randomness
- global mutable state

Use dependency injection or adapters where useful.

## Test levels

Choose the smallest effective level:

### Unit tests

Use for deterministic business logic and pure transformations.

### Integration tests

Use for boundaries such as:

- database access
- filesystem adapters
- external service adapters
- framework integration

### API tests

Use for HTTP contracts, authentication, validation, status codes, and response shapes.

### End-to-end tests

Use for critical user workflows that span multiple application layers.

Do not add expensive end-to-end tests for logic that can be covered reliably with unit tests.

## What to test

Prioritize:

- happy path
- validation failures
- boundary conditions
- authorization failures
- error handling
- regression cases
- important state transitions

For bug fixes, add a regression test that fails before the fix when practical.

## Test isolation

Tests should not depend on execution order.

Avoid shared mutable state between tests.

Clean up resources:

- database records
- temporary files
- servers
- timers
- mocks
- subscriptions

## Async behavior

Await asynchronous operations.

Do not let tests pass because a promise was never awaited.

Explicitly test rejected promises and error paths.

## External services

Do not make unit tests depend on live external services.

Use mocks, fakes, or local test infrastructure according to project conventions.

Keep a smaller number of integration/e2e tests for real boundary behavior.

## Validation workflow

Use existing scripts. Typical checks:

```bash
npm test
npm run lint
npm run typecheck
npm run build
```

Only run commands that exist.

After modifying code, rerun the narrowest relevant check first, then the broader suite.

## CI

When CI exists, ensure local validation approximates CI.

Do not claim success unless the relevant checks actually ran.

If a check cannot be run, report that explicitly.
