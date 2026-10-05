# GetX package guidance

Version information was checked against the official package registry on **2026-10-05**. These are compatible constraints for a new dependency declaration, not a lockfile or a promise that every Flutter/Dart SDK can resolve them. Check the consuming project's SDK constraints and resolver output before adoption.

```yaml
packages:
  - name: get
    purpose: GetX state management, dependency registration, and optional navigation APIs.
    version_constraint: ^4.7.3
    official_source: https://pub.dev/packages/get
    notes: Prefer the stable 4.x release line for this workflow; evaluate prereleases separately.
    verified_on: 2026-10-05
```

Use the package only for capabilities the project selected. GetX being installed does not require GetX navigation or global dependency lookup in every layer.
