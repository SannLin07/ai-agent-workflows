# Supabase Auth package guidance

Verified against authoritative package sources on **2026-10-05**. Constraints are dated recommendations; the consuming project's SDK constraints and lockfile determine the resolved version.

```yaml
packages:
  - name: supabase_flutter
    purpose: Supabase client and auth integration for Flutter
    version_constraint: "^2.18.0"
    official_source: https://pub.dev/packages/supabase_flutter
    notes: >-
      Use public client key only with server-enforced policies.
    verified_on: 2026-10-05
```
