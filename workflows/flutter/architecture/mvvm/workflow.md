# MVVM workflow

Use this module when `mvvm` is selected in the `architecture` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The project wants a view and presentation-model boundary with screen state/actions owned by a ViewModel-like object.

## Avoid when

ViewModel would merely rename a controller without clear lifecycle or ownership.

## Architecture tradeoffs

- Benefits: screen state can be separated from rendering.
- Costs: can duplicate the selected state tool's controller/notifier concepts.
- Complexity: low to medium, depending on lifecycle ownership.
- Typical size: any app with non-trivial screen logic.
- Compatibility: pairs with GetX, Riverpod, BLoC, or Provider; avoid duplicate concepts.

## Agent procedure

1. Keep the View focused on rendering and forwarding intent.
2. Scope each ViewModel to one screen or cohesive flow; do not make it own navigation, persistence, and networking policy at once.
3. Use the selected state tool's observation/lifecycle mechanism rather than mixing mechanisms.
4. Inject collaborators and define who creates and disposes the ViewModel.

## Completion checks

- [ ] Presentation state is testable without rendering the screen.
- [ ] Views contain no business decisions or external I/O.
- [ ] The selected state tool supplies lifecycle and observation.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
