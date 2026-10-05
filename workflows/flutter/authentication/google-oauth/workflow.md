# Google OAuth sign-in workflow

Use this module when `google-oauth` is selected in the `authentication` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

Google identity is a supported sign-in method and platform OAuth clients are configured.

## Avoid when

The app is expected to contain OAuth client secrets or Google identity is not a requirement.

## Agent procedure

1. Configure platform client IDs and redirects using current official setup.
2. Use the platform sign-in flow and exchange credentials with selected backend/Firebase integration.
3. Distinguish ID tokens from scoped access tokens; neither is the app's authorization database.
4. Handle cancellation, revoked consent, expiry, and account linking.
5. Use least privilege and validate identity at the trusted backend.

## Completion checks

- [ ] Platform configuration and redirects work on supported devices.
- [ ] Cancellation and account linking are handled.
- [ ] Tokens are not logged or stored in ordinary preferences.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
