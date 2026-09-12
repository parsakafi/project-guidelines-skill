# Logging Guidelines

## Log for diagnosis, not noise

Use logging that helps diagnose real production issues without exposing sensitive data.

Avoid logging:

- passwords
- secrets
- tokens
- session identifiers
- personal data
- authorization headers
- stack traces in client-visible output

## Production readiness

Prefer readable application logging with useful context such as request IDs, operation names, and error categories when the project already uses them.

Do not leave development-only console output in production code.

If the project uses structured or centralized logging, follow that pattern.

## Errors

Log enough to debug the issue but be careful not to expose internal implementation details to untrusted clients.

Keep detailed diagnostics in protected logs and return safe, minimal client-facing errors.
