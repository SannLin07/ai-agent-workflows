# GetX patterns

## Focused controller

Give each controller one screen or cohesive feature responsibility. Inject collaborators through its constructor when the binding can provide them. Expose state and actions needed by the view; keep request construction, serialization, and persistence in selected networking/storage boundaries.

## Reactive state

Use independent observables when fields can change independently. Group coupled values into one immutable state when they must remain consistent, such as a paginated result and its loading/error status. Keep `Obx` around only the widgets that read those values.

## Dependency binding

Use a route binding to register the controller and feature dependencies. Register app-lifetime dependencies in an app binding and document why they outlive a route. Prefer lazy creation for screen dependencies. Avoid `Get.put` inside `build`, and avoid permanent registrations as a shortcut for lifecycle bugs.

## Request state

Model at least the states the UI needs to distinguish: initial/idle, loading, loaded (including an empty result), and failure. Keep a stale-data refresh state separate when the user can continue viewing existing data while refresh runs. Ignore or cancel an earlier request when a newer input supersedes it.

## Workers

Use `debounce` for user input such as search, `ever` for a persistent reaction that must see every change, and `once` for a one-time transition. Use `interval` only when rate limiting repeated changes is the actual behavior. Store the worker handle and dispose it when manually managed.

## Navigation

Use named routes for app flows that need stable deep links, guards, or centralized route review. Keep route arguments small and serializable when restoration/deep linking matters. Use the selected routing workflow as the source of truth; do not mix router APIs in a single flow.
