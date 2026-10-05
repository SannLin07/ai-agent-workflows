# AI Agent Workflows

A small, versioned library of engineering workflows that a developer can select for each project and give to an AI coding agent. The library starts with Flutter and can grow to other stacks when real projects need them.

It provides reusable instructions. It is not a Flutter starter app, generator, package manager, or agent orchestration system.

## How it works

1. Copy [`config/example-project.yaml`](config/example-project.yaml) into the project as `project.yaml` and edit the selections.
2. Read [`shared/documentation/agent-context-loading.md`](shared/documentation/agent-context-loading.md) to determine the minimum context needed for the task.
3. Load the global rules and only the selected workflow modules. Follow each module's `entrypoint` and recursively load its `requires` modules.
4. Check `conflicts_with`, category cardinality, and the project’s pinned versions before changing code. Ask about unresolved conflicts instead of silently choosing.
5. Apply project-specific rules and the current task, then report which workflow guidance was used and any checks that remain.

The library is a reference for the agent. Copy or link the selected context into each project; this repository does not fetch files or configure agents automatically.

## Select workflows

Selections live in `project.yaml`. State management and routing each have one choice. Architecture, networking, storage, authentication, backend, and test stages can contain multiple IDs when they are intentionally composed.

Deployment targets are selected separately from tester distribution. Unit, widget, and integration describe verification scope; closed and open testing describe Google Play tester access.

```yaml
schema_version: 1
project:
  name: example_app
  platform: [android, ios]
flutter:
  state_management: getx
  architecture: [feature-based]
  networking: [dio]
  routing: getx
  storage: [hive, secure-storage]
  authentication: [firebase-auth, google-oauth]
  backend: [firebase]
testing:
  levels: [unit, widget, integration]
  release_channels: [closed-testing]
deployment:
  targets: [android]
  distribution: [play-store]
workflow_versions:
  flutter.state-management.getx: 0.1.0
  flutter.architecture.feature-based: 0.1.0
  flutter.networking.dio: 0.1.0
  flutter.routing.getx: 0.1.0
  flutter.testing.closed-testing: 0.1.0
  flutter.deployment.android: 0.1.0
  flutter.deployment.play-store: 0.1.0
```

The canonical machine-readable file is each module's `workflow.yaml`; its `entrypoint` names the human- and agent-readable procedure. IDs are stable even if display names change. `requires` names mandatory module IDs. `conflicts_with` names hard conflicts. Optional `compatible_with` is only advisory and never a complete compatibility matrix.

If two architecture modules are selected, the project must state how they compose. For example, feature-based organization can contain clean-architecture layers. A second state-management or routing module is a conflict unless a deliberate migration or isolated boundary is documented.

## How an agent loads context

Start with the global rules and project configuration, then load just the selected modules relevant to the task. For a GetX feature task, that commonly means the GetX state-management workflow, the chosen architecture, and any selected networking, routing, storage, authentication, and testing modules that the change touches. Do not load Riverpod, BLoC, or Provider simply because they exist in this repository.

See [`shared/documentation/agent-context-loading.md`](shared/documentation/agent-context-loading.md) for the full selection order and conflict behavior. Rules are guidance with different strengths; a conflict between explicit project decisions and a workflow MUST is surfaced for resolution. Repository guidance does not supersede platform or higher-priority instructions.

## Repository map

- `config/` — project configuration schema and a working example.
- `shared/` — rules that apply across selected technologies.
- `workflows/flutter/` — focused, independently versioned Flutter modules.
- `templates/` — starter documents for project records.
- `troubleshooting/` — evidence-based incident records; currently an empty knowledge base.
- `scripts/` — future tooling notes only; there is no generator or workflow engine.
- `VERSION` — release version for this collection. Module versions evolve independently.

## Available Flutter modules

- State management: [GetX](workflows/flutter/state-management/getx/workflow.md), [Riverpod](workflows/flutter/state-management/riverpod/workflow.md), [BLoC/Cubit](workflows/flutter/state-management/bloc/workflow.md), [Provider](workflows/flutter/state-management/provider/workflow.md).
- Architecture: [feature-based](workflows/flutter/architecture/feature-based/workflow.md), [clean architecture](workflows/flutter/architecture/clean-architecture/workflow.md), [layered](workflows/flutter/architecture/layered/workflow.md), [MVVM](workflows/flutter/architecture/mvvm/workflow.md).
- Networking: [Dio](workflows/flutter/networking/dio/workflow.md), [http](workflows/flutter/networking/http/workflow.md), [Retrofit](workflows/flutter/networking/retrofit/workflow.md).
- Routing: [GetX](workflows/flutter/routing/getx/workflow.md), [GoRouter](workflows/flutter/routing/go-router/workflow.md).
- Storage: [Hive-compatible](workflows/flutter/storage/hive/workflow.md), [Shared Preferences](workflows/flutter/storage/shared-preferences/workflow.md), [Secure Storage](workflows/flutter/storage/secure-storage/workflow.md), [SQLite](workflows/flutter/storage/sqlite/workflow.md).
- Authentication: [Firebase Auth](workflows/flutter/authentication/firebase-auth/workflow.md), [Google OAuth](workflows/flutter/authentication/google-oauth/workflow.md), [JWT sessions](workflows/flutter/authentication/jwt/workflow.md), [Supabase Auth](workflows/flutter/authentication/supabase-auth/workflow.md).
- Backend: [REST API contracts](workflows/flutter/backend/rest-api/workflow.md), [FastAPI](workflows/flutter/backend/fastapi/workflow.md), [Firebase](workflows/flutter/backend/firebase/workflow.md).
- Testing: [unit](workflows/flutter/testing/unit/workflow.md), [widget](workflows/flutter/testing/widget/workflow.md), [integration](workflows/flutter/testing/integration/workflow.md), [closed testing](workflows/flutter/testing/closed-testing/workflow.md), [open testing](workflows/flutter/testing/open-testing/workflow.md).
- Deployment: [Android](workflows/flutter/deployment/android/workflow.md), [iOS](workflows/flutter/deployment/ios/workflow.md), [Google Play](workflows/flutter/deployment/play-store/workflow.md).

## Templates

Start from the relevant file in `templates/`: [project config and agent context](templates/project/), [feature brief](templates/feature/feature-brief.md), [bug report](templates/bug-report/bug-report.md), [troubleshooting record](templates/troubleshooting/troubleshooting-record.md), [architecture decision](templates/architecture-decision/adr.md), [code review](templates/code-review/code-review.md), or [release checklist](templates/release/release-checklist.md).

## Add a workflow

1. Add `workflows/<platform>/<category>/<slug>/workflow.yaml` and `workflow.md`.
2. Give the module a stable ID, a short task-oriented entrypoint, an independent `0.x.y` version, and only real `requires` or hard conflicts.
3. Keep shared rules in `shared/`; link to them instead of copying them into each module.
4. Add package guidance only when the module depends on a package choice. Record a compatible constraint, authoritative source, purpose, notes, and verification date.
5. Update the project schema/example if the module becomes selectable, and add a real compatibility note only when there is a concrete constraint.

Each workflow should say when to use it, what to do, what to verify, and when it does not apply. See [`CONTRIBUTING.md`](CONTRIBUTING.md) for update and review guidance.

## Versions

The root `VERSION` versions the collection. Each `workflow.yaml` versions its module. A project may pin only the modules it relies on through `workflow_versions`. Use semantic versioning: patch for clarifications and corrections that do not change expected behavior, minor for backward-compatible additions, and major for breaking changes to selection or required behavior. Initial unpiloted workflows are `0.1.0` with `status: draft`; promote them after a real project validates their guidance.

## Grow from evidence

Add troubleshooting records only after a problem has been observed and investigated. Keep hypotheses distinct from confirmed causes and include environment, exact evidence, the fix, and verification. Do not populate the knowledge base with invented cases.

## Future direction

The intended manual loop is: project configuration → selected metadata → relevant workflows and global rules → implementation → validation → verified lessons. A loader or validator may be useful after repeated manual use, but this repository currently has no automation engine.
