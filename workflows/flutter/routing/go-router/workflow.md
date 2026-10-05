# GoRouter workflow

Use this module when `go-router` is selected in the `routing` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The app needs declarative routing, URL/deep-link support, nested navigation, or centralized redirects.

## Avoid when

A one-flow prototype gains no value from extra router configuration.

## Agent procedure

1. Define stable named paths and validate typed/path/query parameters.
2. Base redirects on explicit auth-loading/authenticated/unauthenticated state and prevent loops.
3. Keep navigation decisions in the router or a small boundary.
4. Use nested navigators when independent tab history is a real UX need.
5. Treat deep-link values as untrusted; test redirects, unknown routes, and back behavior.

## Completion checks

- [ ] Paths/names are unique and parameters validated.
- [ ] Auth redirects do not loop.
- [ ] Deep links work on configured targets.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
