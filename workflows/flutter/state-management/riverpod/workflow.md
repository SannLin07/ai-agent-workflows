# Riverpod workflow

Use this module when `riverpod` is selected in the `state-management` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The project selects Riverpod for provider-based state and dependency composition, especially when dependencies should be easy to override in tests.

## Avoid when

The project already has another primary state tool, or the feature only needs local widget state.

## Agent procedure

1. Add ProviderScope at the app boundary once.
2. Use Provider for simple dependencies or derived values, Notifier for synchronous mutable feature state, and AsyncNotifier for asynchronous state.
3. Keep providers near the feature owner; inject repositories through providers and override them with fakes in tests.
4. Use ref.watch for rendering and ref.read for callbacks. Represent loading, data (including empty data), and errors explicitly with AsyncValue.
5. Invalidate or refresh dependent providers after successful mutations.

## Completion checks

- [ ] Notifier transitions and async outcomes have unit tests.
- [ ] Widget tests override dependencies and assert visible loading, data, and error states.
- [ ] No GetX, BLoC, or Provider state layer was added without an explicit bounded reason.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
