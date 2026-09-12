# Security Guidelines

Treat security as a design constraint, not a final review step.

## Trust boundaries

Treat all external data as untrusted:

- HTTP requests
- query strings
- form fields
- JSON
- headers
- cookies
- uploaded files
- webhooks
- third-party API responses
- environment/configuration values when user-controlled

Validate at trust boundaries.

## Secrets

Never commit or hard-code:

- passwords
- API keys
- private keys
- access tokens
- refresh tokens
- webhook secrets
- database credentials

Never place secrets in logs.

Use environment/configuration mechanisms already established by the project.

If a secret is accidentally exposed, do not merely delete it from the current file. Recommend rotation/revocation as appropriate.

## Authentication

Authentication must be enforced server-side.

Validate:

- token signature
- issuer/audience when applicable
- expiration
- required claims
- token type

Do not trust client-provided identity fields when the authenticated identity is available from the authentication context.

## Authorization

Authentication does not imply authorization.

For protected resources, verify that the authenticated principal has permission to perform the requested operation.

Check authorization at the server/resource boundary.

Avoid insecure direct object references such as accepting an object ID and returning it without permission checks.

## Input validation

Validate type, format, range, length, and allowed values.

Prefer allowlists for constrained values.

Do not rely only on client-side validation.

## Injection

Protect against:

- SQL injection
- NoSQL injection
- command injection
- template injection
- LDAP injection
- XSS
- path traversal

Use parameterized queries or the safe abstraction provided by the database library.

Never concatenate untrusted input into shell commands, SQL, HTML, or executable code.

## XSS

Escape untrusted output according to its context.

Do not render arbitrary HTML unless it is deliberately sanitized and the security model permits it.

Avoid unsafe DOM APIs such as raw `innerHTML` for untrusted content.

## SSRF

For server-side requests based on user input:

- validate destination URLs
- restrict protocols
- restrict hosts/IP ranges where appropriate
- prevent access to internal/private network targets
- consider redirect handling
- apply timeouts and response-size limits

Do not assume a URL is safe merely because it uses HTTPS.

## CSRF

For cookie-authenticated state-changing requests, use an appropriate CSRF defense.

SameSite cookies can help but should not automatically be treated as the sole defense for every threat model.

## Rate limiting

Consider rate limits for:

- login
- password reset
- verification
- expensive operations
- public APIs

Use stronger controls for authentication endpoints.

## Passwords

Never store plaintext passwords.

Use a modern password hashing algorithm supported by the project's ecosystem.

Never log passwords.

Do not send passwords back in API responses.

## Cookies

For sensitive authentication cookies, consider:

```text
Secure
HttpOnly
SameSite
```

Use an appropriate domain/path scope.

## HTTP security

Production applications should use HTTPS.

Use appropriate security headers for the application architecture.

Do not expose unnecessary server/framework version information.

## Dependencies

Keep dependencies current enough to receive security fixes.

Review dependency advisories before upgrades.

Avoid adding packages with unclear provenance or unnecessary privilege.

## Logging and privacy

Log enough information to diagnose failures without exposing:

- credentials
- tokens
- session identifiers
- sensitive personal information
- payment data

Apply data minimization.

## File uploads

If accepting uploads:

- validate file size
- validate allowed types
- do not trust filename extensions
- generate safe storage names
- prevent executable uploads
- store outside the executable web root when appropriate
- scan content where required
- enforce authorization

## Error handling

Return safe client-facing errors.

Keep detailed diagnostics in protected server logs.

Never expose stack traces or internal configuration in production API responses.

## Security review checklist

Before finishing security-sensitive work, check:

- authentication
- authorization
- validation
- injection
- XSS
- CSRF
- SSRF
- secrets
- logging
- dependency risk
- rate limiting
- error exposure
- file handling
