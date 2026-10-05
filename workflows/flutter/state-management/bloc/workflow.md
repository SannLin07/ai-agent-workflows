# BLoC / Cubit workflow

Use this module when `bloc` is selected in the `state-management` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The project values explicit state transitions, event-driven flows, or a clear boundary between UI intent and resulting state.

## Avoid when

The feature is tiny local widget state or the app has standardized on another state tool.

## Agent procedure

1. Use Cubit for direct named actions and a compact state model; use Bloc events when explicit inputs improve traceability or concurrency policy.
2. Define immutable states for meaningful UI states; keep widgets focused on rendering and forwarding intent.
3. Call repositories through the Bloc/Cubit boundary; construct dependencies at the composition root.
4. Choose explicit overlap or cancellation policy for concurrent events; close owned streams and resources.

## Completion checks

- [ ] Tests cover important action/event-to-state behavior, including failure.
- [ ] Widget tests verify user intent produces expected visible state.
- [ ] No second primary state library was introduced without a migration boundary.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
