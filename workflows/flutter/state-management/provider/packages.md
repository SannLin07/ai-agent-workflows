# Provider package guidance

Verified against authoritative package sources on **2026-10-05**. Constraints are dated recommendations; the consuming project's SDK constraints and lockfile determine the resolved version.

```yaml
packages:
  - name: provider
    purpose: Dependency injection and ChangeNotifier integration
    version_constraint: ^6.1.5+1
    official_source: https://pub.dev/packages/provider
    notes: >-
      Use Flutter SDK primitives when Provider adds no useful boundary.
    verified_on: 2026-10-05
```
