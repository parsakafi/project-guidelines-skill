# Environments and Configuration Guidelines

## Keep environments consistent

Use a consistent local runtime version and dependency lockfile.

Prefer project-established conventions for:

- Node.js version
- package manager
- lockfile
- environment files
- config layout
- startup validation

If a repository uses `.nvmrc`, `engines`, or a package manager lockfile, honor it.

## Configuration

Keep runtime-specific values out of source code.

Use environment variables for:

- API endpoints
- secrets
- tokens
- credentials
- feature flags
- local/test/prod differences

Prefer a committed example file such as `.env.example` if the project needs documented placeholders.

## Separate environments intentionally

Use separate development, test, and production configuration when needed.

Do not split config by environment in an ad hoc or unscalable way unless the repository already follows that pattern.

## Validation

Validate required configuration at startup when practical, especially for required secrets or URLs.

Fail early with clear errors instead of allowing startup to proceed with incomplete configuration.
