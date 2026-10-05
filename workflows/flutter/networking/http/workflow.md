# Dart http client workflow

Use this module when `http` is selected in the `networking` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The app needs straightforward HTTP requests and a small explicit client abstraction.

## Avoid when

Advanced interceptors or cancellation are required, or the project standardized on Dio.

## Agent procedure

1. Wrap http.Client behind an injected API/repository boundary.
2. Set timeouts and handle non-success status codes explicitly.
3. Parse and validate response shapes at the data boundary.
4. Pass auth from the selected session source and redact it from diagnostics.
5. Close clients with their owner; retry only transient safe operations.

## Completion checks

- [ ] Success, error status, timeout, and malformed response are covered.
- [ ] Tests use a fake client or controlled endpoint.
- [ ] No duplicate client stack was added without a decision.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
