# Provider workflow

Use this module when `provider` is selected in the `state-management` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The project needs a small Flutter-native dependency and ChangeNotifier layer and its simplicity fits the app.

## Avoid when

State transitions, concurrent async flows, or dependency graphs have outgrown the team's ability to keep ChangeNotifier clear.

## Agent procedure

1. Use ChangeNotifier for modest mutable presentation state; keep notifications intentional and never notify during build.
2. Use ChangeNotifierProvider to own objects it creates and value providers only for externally owned objects.
3. Use context.watch or Consumer for rendering, context.read for actions, and select when one field is sufficient.
4. Inject data collaborators and represent async loading and error explicitly.

## Completion checks

- [ ] Tests cover state changes and relevant notifications.
- [ ] Widget tests assert user-visible results.
- [ ] ChangeNotifier state remains small and understandable.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
