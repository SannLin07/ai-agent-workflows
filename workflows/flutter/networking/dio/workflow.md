# Dio HTTP client workflow

Use this module when `dio` is selected in the `networking` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The client needs shared HTTP configuration with timeouts, interceptors, cancellation, or consistent response handling.

## Avoid when

Only a few simple requests exist and the SDK http package fits.

## Agent procedure

1. Configure a shared client with base URL and explicit timeouts at the data boundary.
2. Map transport and response failures into safe app errors in one place.
3. Use interceptors for headers and observability; redact credentials and personal data.
4. Coordinate token refresh to avoid parallel refresh storms; retry only safe operations.
5. Cancel abandoned requests and inject the client/API boundary for tests.

## Completion checks

- [ ] Timeout, error mapping, auth header, and cancellation are covered.
- [ ] Logs do not expose secrets or payloads.
- [ ] Tests use controlled endpoints or fake adapters.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
