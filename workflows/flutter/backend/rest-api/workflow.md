# REST API contract workflow

Use this module when `rest-api` is selected in the `backend` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The Flutter client communicates with a backend through resource-oriented HTTP endpoints.

## Avoid when

A managed SDK already covers the product or a streaming/RPC protocol fits better.

## Agent procedure

1. Define schemas, auth, status codes, pagination, and stable error shape.
2. Authorize every protected request on the server over HTTPS.
3. Use safe method semantics or idempotency for client retries.
4. Version contracts deliberately and add contract tests for serialization, auth, and failures.
5. Do not expose stack traces or secrets in client-visible errors.

## Completion checks

- [ ] Success, validation, auth, missing/conflict, and server-error behavior is specified.
- [ ] Authorization is enforced per resource/action.
- [ ] The client maps transport errors to safe app errors.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
