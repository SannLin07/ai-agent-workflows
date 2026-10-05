# FastAPI backend package guidance

Verified against authoritative package sources on **2026-10-05**. Constraints are dated recommendations; the consuming project's SDK constraints and lockfile determine the resolved version.

```yaml
packages:
  - name: fastapi
    purpose: Python ASGI framework with validation and OpenAPI
    version_constraint: ">=0.142.2,<0.143.0"
    official_source: https://pypi.org/project/fastapi/
    notes: >-
      Use the Python dependency manager and lockfile; verify Python and Pydantic compatibility.
    verified_on: 2026-10-05
```
