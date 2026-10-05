# FastAPI backend workflow

Use this module when `fastapi` is selected in the `backend` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The Flutter app pairs with a Python API and the team wants typed request validation and OpenAPI.

## Avoid when

The backend is standardized elsewhere or a managed service is sufficient.

## Agent procedure

1. Keep route handlers thin; separate boundary schemas from database entities as needed.
2. Validate authentication and authorization through trusted dependencies.
3. Use async handlers only with async I/O; scope database sessions and transactions deliberately.
4. Restrict browser CORS; CORS is not authentication.
5. Review OpenAPI changes and keep secrets in deployment configuration.

## Completion checks

- [ ] Success, validation, auth denial, and expected failures are tested.
- [ ] Resource and transaction lifetimes are bounded.
- [ ] Production secrets and tracebacks are not exposed.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Official references

- [Official reference 1](https://fastapi.tiangolo.com/)

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
