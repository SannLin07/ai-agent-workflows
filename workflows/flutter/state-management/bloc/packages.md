# BLoC / Cubit package guidance

Verified against authoritative package sources on **2026-10-05**. Constraints are dated recommendations; the consuming project's SDK constraints and lockfile determine the resolved version.

```yaml
packages:
  - name: flutter_bloc
    purpose: Flutter widgets and dependency helpers for Bloc/Cubit
    version_constraint: ^9.1.1
    official_source: https://pub.dev/packages/flutter_bloc
    notes: >-
      Use Bloc for explicit event streams and Cubit for direct actions.
    verified_on: 2026-10-05
```
