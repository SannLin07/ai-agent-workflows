# Retrofit generated API client workflow

Use this module when `retrofit` is selected in the `networking` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The project has enough typed endpoints to benefit from generated declarations over Dio.

## Avoid when

A tiny API surface is clearer with handwritten calls or code generation is not maintained.

## Agent procedure

1. Use Retrofit declarations over the selected Dio client; keep timeouts, auth, and error policy in Dio setup.
2. Keep DTOs at the API boundary and convert to domain shapes when needed.
3. Run the documented generator after annotation changes; review output and never hand-edit generated files.
4. Inject the API behind a repository boundary.
5. Mock the repository for most tests and add focused serialization/contract coverage.

## Completion checks

- [ ] Generated source is reproducible and committed by project policy.
- [ ] Serialization and API errors are tested at the boundary.
- [ ] Auth refresh and safe retry remain in shared Dio setup.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
