# Firebase backend services workflow

Use this module when `firebase` is selected in the `backend` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The product benefits from specific managed Firebase services.

## Avoid when

Relational/custom server guarantees or portability outweigh the managed-service fit.

## Agent procedure

1. Choose each service for a concrete need and review data/access limits.
2. Treat Security Rules as authorization code: deny by default and test allowed and denied access.
3. Keep Admin SDK/service-account access on trusted servers only.
4. Separate development, staging, and production projects and confirm target before deploy.
5. Define offline/cache, deletion, retention, and export behavior.

## Completion checks

- [ ] Rules are tested with allowed and denied identities.
- [ ] No privileged key is in the client bundle.
- [ ] Environments and data lifecycle are documented.

## Official references

- [Official reference 1](https://firebase.google.com/docs)

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
