# GetX folder structure

Keep feature code together and place GetX roles in each feature. This makes a feature's view, controller, bindings, and data boundary discoverable without imposing the same layout on every app.

```text
lib/
  app/
    app.dart
    routes/
      app_pages.dart
      app_routes.dart
    bindings/
      app_binding.dart
    theme/
  core/
    errors/
    network/          # only when networking is selected
    utils/
  features/
    auth/
      bindings/
      controllers/
      views/
      widgets/
      models/          # use project domain/data boundaries where needed
      services/        # keep external I/O behind the chosen architecture
```

For a small feature, begin with only `controllers/`, `views/`, and `bindings/`. Add repositories, domain entities, use cases, or data sources when the feature has meaningful business rules or external boundaries. If clean architecture is selected, use its layer boundaries inside the feature; do not duplicate a second app-wide structure. If MVVM is selected, use the project's ViewModel terminology consistently instead of making `Controller` mean two different roles.

Place app-wide GetX registrations in the app binding only when multiple routes truly share the lifetime. Put route-specific controllers and repositories in the route's binding so their lifecycle follows the route.
