# Hive-compatible local object storage package guidance

Verified against authoritative package sources on **2026-10-05**. Constraints are dated recommendations; the consuming project's SDK constraints and lockfile determine the resolved version.

```yaml
packages:
  - name: hive_ce
    purpose: Community-maintained Hive-compatible local boxes
    version_constraint: ^2.20.1
    official_source: https://pub.dev/packages/hive_ce
    notes: >-
      Original hive stable 2.2.3 is old; hive_ce is a community continuation with its own migration considerations.
    verified_on: 2026-10-05
  - name: hive_ce_flutter
    purpose: Flutter helpers for Hive CE
    version_constraint: ^2.4.0
    official_source: https://pub.dev/packages/hive_ce_flutter
    notes: >-
      Use when Flutter-specific setup is needed.
    verified_on: 2026-10-05
```
