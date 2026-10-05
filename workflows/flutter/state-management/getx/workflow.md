# GetX state management workflow

Use this module when `flutter.state_management` is `getx`. It guides application state and dependency organization; it does not require every widget, route, or service to use GetX. Read the selected architecture and routing modules as well when the task touches those boundaries.

## Use GetX when

- The project already uses GetX consistently, or the team values its integrated reactive state, dependency registration, and navigation APIs.
- A feature benefits from a controller that can expose observable state and coordinate presentation actions.
- The team accepts the coupling to GetX conventions and can keep controllers focused.

Choose another state approach when the project has already standardized on it, when explicit event/state boundaries are central to the product, or when GetX's combined APIs would obscure ownership. Do not migrate an established project as incidental cleanup.

## Agent procedure

1. Confirm this workflow is selected and inspect existing feature patterns before adding another. Check project configuration for architecture and routing choices.
2. Read `folder-structure.md` and follow the existing project variation. Create only the folders the feature needs.
3. Keep widget rendering in views, feature decisions and presentation state in a focused `GetxController`, and I/O behind the selected repository/service boundary. Do not let a controller become a general-purpose service locator or contain transport parsing.
4. Register route-scoped dependencies in a `Bindings` class. Use lazy registration for feature dependencies when appropriate; use permanent/global registrations only for genuinely app-wide lifetime.
5. Define route names/pages centrally in the app routing area when GetX routing is selected. Pass small route arguments or IDs; resolve durable data through the feature boundary. If `go-router` is selected, use that router's navigation API and keep GetX limited to state/dependency work.
6. Model user-visible async work with explicit loading, success/data, empty, and failure states. Use reactive variables for small focused values and an immutable state object when values must change together.
7. Use GetX workers only for a real reaction to changes, such as debouncing a search query. Dispose workers and subscriptions with the controller lifecycle.
8. Add controller unit tests for state transitions and side effects, widget tests for visible interaction, and integration coverage for important cross-boundary flows. See `testing.md`.
9. Review `checklist.md` and report the selected boundaries, tests run, and any intentional deviation.

## State and lifecycle rules

- Use `final Rx<T>` / `.obs` for observable values that need independent updates; prefer `RxList`, `RxMap`, or `RxSet` only when collection mutation is part of the feature's behavior.
- Use `Obx` for a small reactive region and `GetX<T>` when a typed controller binding is useful. Keep reactive rebuild regions narrow.
- Change state through named controller methods. Avoid exposing mutable internals that arbitrary widgets can update.
- Keep constructors and controller initialization deterministic. Start async work from an explicit lifecycle hook or action and expose its state; do not hide a request in a widget build.
- Cancel timers, workers, stream subscriptions, and manually owned resources when the controller is closed. Let GetX dispose dependencies it owns; do not dispose the same object twice.
- Treat `Get.find` as a composition-boundary lookup. Prefer constructor injection inside domain/data classes so unit tests can supply fakes directly.
- Do not keep transient screen state globally. Use route-scoped controllers for screen state and app-scoped bindings only for shared app services.
- Do not introduce a second state-management package for new feature state unless the project decision explicitly permits a bounded migration or integration.

## Async API and forms

- Represent request status explicitly; do not infer loading from `data == null` when null is valid data.
- Prevent duplicate submissions when the action is not safely repeatable. Restore controls after success or failure according to the user flow.
- Preserve field values and validation errors on recoverable failures. Keep API/domain errors out of widget code.
- Debounce or cancel superseded search requests so stale responses cannot overwrite newer results.
- For token refresh, retries, and request errors, follow the selected networking and authentication modules rather than implementing transport policy in a controller.
- For forms, keep validation close to the feature and make submit state explicit. Use Flutter form controls where they satisfy the requirement; do not add a form package solely to integrate with GetX.

## References

- [Recommended structure](folder-structure.md)
- [Implementation patterns](patterns.md)
- [Controller testing](testing.md)
- [Package guidance](packages.md)
- [Implementation checklist](checklist.md)

Global coding, security, error handling, logging, and dependency rules apply from `shared/`.
