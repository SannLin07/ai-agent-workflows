# Firebase Authentication package guidance

Verified against authoritative package sources on **2026-10-05**. Constraints are dated recommendations; the consuming project's SDK constraints and lockfile determine the resolved version.

```yaml
packages:
  - name: firebase_core
    purpose: Firebase initialization for Flutter
    version_constraint: "^4.15.0"
    official_source: https://pub.dev/packages/firebase_core
    notes: >-
      Keep environment configuration and credentials out of version control.
    verified_on: 2026-10-05
  - name: firebase_auth
    purpose: Firebase Authentication for Flutter
    version_constraint: "^6.7.0"
    official_source: https://pub.dev/packages/firebase_auth
    notes: >-
      See Firebase official Flutter auth and account-linking docs.
    verified_on: 2026-10-05
```
