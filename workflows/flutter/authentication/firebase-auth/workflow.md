# Firebase Authentication workflow

Use this module when `firebase-auth` is selected in the `authentication` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

Firebase Auth providers and account lifecycle fit the product.

## Avoid when

Another backend is authoritative without a federation plan, or required platform/provider support is absent.

## Agent procedure

1. Initialize with environment-specific configuration; never commit service-account or private keys.
2. Subscribe to auth state at a clear app boundary and map events into selected state management.
3. Link credentials to an existing account when adding providers; avoid duplicate accounts and data loss.
4. Treat client identity as UX: enforce authorization in trusted backend or Firebase Security Rules.
5. Handle expiry, reauthentication, account deletion, cancellation, and sign-out.

## Completion checks

- [ ] Sign-in, expiry, denial, sign-out, and account linking are considered.
- [ ] Protected resources are authorized server-side or with Rules.
- [ ] Test configuration cannot reach production.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Official references

- [Official reference 1](https://firebase.google.com/docs/auth/flutter/start)
- [Official reference 2](https://firebase.google.com/docs/auth/flutter/account-linking)

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
