# JavaScript and Node.js Guidelines

## Repository conventions first

Inspect:

- `package.json`
- lockfile
- runtime/version files
- ESLint configuration
- formatter configuration
- TypeScript/JSDoc configuration
- build configuration
- test configuration

Follow the project's established conventions.

## Naming

Prefer descriptive names.

Good:

```js
calculateMonthlyRevenue()
validateRequest()
loadConfiguration()
```

Avoid unnecessary abbreviations and vague names such as:

```text
data
thing
temp
helper
foo
bar
```

unless the local context makes them genuinely clear.

Functions should usually describe an action.

## Modules and responsibilities

Keep modules focused on a coherent responsibility.

Prefer feature-oriented organization when it fits the application:

```text
src/
  users/
    user.js
    user.test.js
  products/
    product.js
    product.test.js
```

Do not reorganize an existing project solely to enforce this layout.

Avoid large modules containing unrelated business logic, infrastructure, and presentation concerns.

## Modern JavaScript

For new code:

- prefer `const`
- use `let` only when reassignment is needed
- avoid unnecessary mutation
- prefer modules over global state
- use `async`/`await` where it improves clarity
- follow the existing ESM/CommonJS convention

Do not perform broad syntax modernization during an unrelated task.

## Functions

Prefer small functions with clear responsibilities.

Keep business logic separate from I/O and other side effects when practical.

This improves testability and makes failures easier to isolate.

## Error handling

Handle errors at the appropriate boundary.

Do not silently swallow failures.

Avoid:

```js
try {
  doSomething();
} catch {}
```

unless ignoring the error is deliberate and documented.

Preserve useful error context when wrapping errors.

Do not expose internal stack traces or sensitive implementation details to untrusted clients.

## Configuration

Do not hard-code:

- credentials
- API keys
- tokens
- environment-specific URLs
- deployment secrets

Use environment/configuration mechanisms already established by the project.

Validate required configuration during startup when practical.

Keep `.env.example` documentation free of real secrets.

## Dependencies

Before adding a dependency, verify:

- necessity
- maintenance status
- runtime compatibility
- license
- security posture
- package size/cost
- whether the repository already has an equivalent

Avoid duplicate libraries.

## Logging

Do not leave development debugging logs in production code.

Never log:

- passwords
- access tokens
- refresh tokens
- API keys
- authorization headers
- sensitive personal data

Use structured/application logging where the project's complexity warrants it.

## Comments

Comments should explain intent, constraints, or non-obvious decisions.

Do not use comments to compensate for unclear code.

Remove stale comments and commented-out implementation.

## TODOs

Small follow-ups may use:

```js
// TODO(#123): Replace temporary implementation.
```

Use an issue/reference for substantial work instead of leaving a vague TODO.

## Tooling

Use existing linting and formatting.

Do not introduce a new formatter or linter if the repository already has an equivalent without a concrete reason.

Do not suppress lint rules casually. Every suppression should have a legitimate reason.
