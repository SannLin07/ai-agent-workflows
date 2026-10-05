# Hive-compatible local object storage workflow

Use this module when `hive` is selected in the `storage` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The project needs local key/value or object boxes and accepts the Hive Community Edition line.

## Avoid when

Relational queries/transactions are needed, or original hive 2.x compatibility is required without a continuation migration.

## Agent procedure

1. Choose whether data is cache, durable user data, or secret before selecting a box.
2. Initialize storage before features need it and keep access behind a repository boundary.
3. Define stable type adapters and migrations for persisted model changes.
4. Handle corruption and migration errors as recoverable data failures.
5. Use secure storage for credentials and define offline/sync semantics separately.

## Completion checks

- [ ] Initialization, serialization, and migration are covered.
- [ ] Secrets are stored elsewhere.
- [ ] Corruption/recovery behavior is defined.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
