# Retrofit generated API client package guidance

Verified against authoritative package sources on **2026-10-05**. Constraints are dated recommendations; the consuming project's SDK constraints and lockfile determine the resolved version.

```yaml
packages:
  - name: retrofit
    purpose: Typed REST client declarations over Dio
    version_constraint: ^4.10.0
    official_source: https://pub.dev/packages/retrofit
    notes: >-
      Keep generated APIs behind a data boundary.
    verified_on: 2026-10-05
  - name: retrofit_generator
    purpose: Generates Retrofit implementations
    version_constraint: ^10.2.11
    official_source: https://pub.dev/packages/retrofit_generator
    notes: >-
      Development dependency; check analyzer compatibility.
    verified_on: 2026-10-05
  - name: build_runner
    purpose: Runs Dart source generators
    version_constraint: ^2.16.1
    official_source: https://pub.dev/packages/build_runner
    notes: >-
      Use the project's documented generation command.
    verified_on: 2026-10-05
```
