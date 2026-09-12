# REST API Guidelines

Use these guidelines when designing, implementing, or reviewing HTTP APIs.

## Resource-oriented URLs

Prefer plural resource names:

```text
/users
/products
/orders
```

Use nested resources when the relationship is meaningful:

```text
/schools/2/students
/schools/2/students/31
```

Prefer resource-oriented operations:

```text
POST   /users
GET    /users/123
PATCH  /users/123
DELETE /users/123
```

Avoid CRUD verbs in URLs:

```text
/createUser
/updateUser
/deleteUser
```

Action endpoints can be appropriate for operations that are not naturally CRUD/resource representations.

## HTTP methods

Use methods consistently:

```text
GET     retrieve
POST    create/action
PUT     replace
PATCH   partial update
DELETE  delete
```

Respect method semantics and idempotency.

## Status codes

Use standard status codes appropriately:

```text
200 OK
201 Created
204 No Content
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
409 Conflict
422 Unprocessable Content
429 Too Many Requests
500 Internal Server Error
```

Do not invent HTTP status codes.

## Versioning

For public APIs, use the versioning strategy established by the project.

A URL-based strategy can use:

```text
/v1/users
```

Do not introduce versioning into an existing API without considering compatibility and project conventions.

## JSON

For JavaScript APIs, prefer `camelCase` unless the API already uses another established convention.

Example:

```json
{
  "firstName": "John",
  "createdAt": "2026-09-12T00:00:00Z"
}
```

Do not leak database implementation details into the public API accidentally.

## Validation

Validate:

- path parameters
- query parameters
- request body
- headers
- content type
- authentication data

Treat all client input as untrusted.

Reject malformed input with an appropriate 4xx response.

## Errors

Use a consistent error representation.

Example:

```json
{
  "code": "VALIDATION_ERROR",
  "message": "Request validation failed",
  "details": []
}
```

Do not expose stack traces, SQL errors, filesystem paths, secrets, or internal implementation details.

## Pagination

For collection endpoints, implement pagination where result sets can grow.

Use the project's established strategy, such as:

```text
?limit=20&offset=40
```

or cursor pagination.

Document pagination behavior.

## Filtering and sorting

Add filtering/sorting only where useful.

Validate allowed fields and operators.

Never turn arbitrary client-provided strings directly into database queries or sort expressions.

## Authentication

Prefer standard authentication mechanisms.

For bearer tokens:

```http
Authorization: Bearer <token>
```

Never put access tokens in URLs.

Use TLS in production.

## API documentation

Document:

- method
- path
- authentication
- parameters
- request body
- response body
- status codes
- validation rules
- examples

For sufficiently complex APIs, use OpenAPI or the project's equivalent.

## Compatibility

Avoid breaking public contracts accidentally.

When changing:

- field names
- required fields
- status codes
- authentication
- pagination
- error formats

consider versioning, migration, or backward compatibility.
