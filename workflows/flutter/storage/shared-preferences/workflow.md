# Shared Preferences workflow

Use this module when `shared-preferences` is selected in the `storage` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The app needs small, non-sensitive scalar preferences such as onboarding or display choices.

## Avoid when

Passwords/tokens, large objects, transactions, or relational queries are involved.

## Agent procedure

1. Centralize typed keys behind a small settings repository.
2. Treat values as optional and provide defaults for absent/invalid values.
3. Use async APIs and do not block startup on low-value preferences.
4. Do not store secrets or authoritative business records.

## Completion checks

- [ ] Only small non-sensitive settings are stored.
- [ ] Renamed keys have a default/migration strategy.
- [ ] Tests cover missing and persisted values.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
