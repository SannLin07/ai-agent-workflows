# Secure Storage workflow

Use this module when `secure-storage` is selected in the `storage` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

A small credential or secret must persist through platform-backed secure storage.

## Avoid when

Ordinary cache/preferences or large database data is involved.

## Agent procedure

1. Store only minimum secret material; prefer short-lived access tokens in memory when practical.
2. Use an injected secure-storage boundary and handle locked/unavailable storage.
3. Clear correct keys on sign-out/account switch.
4. Keep secrets out of logs, routes, crash reports, and unreviewed backups.
5. Review current platform configuration and migration behavior.

## Completion checks

- [ ] Secrets are absent from logs, source, and ordinary preferences.
- [ ] Sign-out clears intended credentials.
- [ ] Platform backup and keychain behavior are reviewed.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
