# SQLite database workflow

Use this module when `sqlite` is selected in the `storage` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The app needs structured local records, indexed queries, relations, or transactions.

## Avoid when

Data is only a preference, tiny cache, or secret.

## Agent procedure

1. Define schema and migration paths for supported stored versions.
2. Keep SQL, mapping, transactions, and queries behind the data boundary.
3. Use parameters and transactions for multi-step updates.
4. Choose indexes from measured access patterns and define deletion/privacy behavior.

## Completion checks

- [ ] Fresh install and upgrade migrations are tested.
- [ ] Queries are parameterized and critical multi-record changes are transactional.
- [ ] Failure and deletion behavior are defined.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
