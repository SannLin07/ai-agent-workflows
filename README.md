# AI Agent Workflows

A versioned library of Flutter engineering workflows that a developer can select for each Flutter project and give to an AI coding agent. Its main scope is Flutter app development. Optional backend modules provide guidance for API and service boundaries that a Flutter app uses when those integrations are part of the project.

It provides reusable instructions. It is not a Flutter starter app, generator, package manager, or agent orchestration system.

## How it works

1. Copy [`config/example-project.yaml`](config/example-project.yaml) into the Flutter project as `project.yaml`. Select the app's platforms and the workflows it actually uses, then pin the adopted module versions when the project needs reproducible guidance.
2. Read the Flutter project's local instructions, accepted decisions, and existing conventions. Then use [`shared/documentation/agent-context-loading.md`](shared/documentation/agent-context-loading.md) to identify the smallest set of guidance that applies to the task.
3. Load the relevant shared rules and selected workflow entrypoints. Follow each module's `entrypoint` and recursively load its required modules so mandatory guidance is not missed.
4. Check `conflicts_with`, category cardinality, architecture composition, and the project's pinned versions before implementation. Surface unresolved conflicts instead of choosing a technology silently.
5. Implement the requested behavior within the project's established boundaries. Verify it against acceptance criteria and applicable workflow checks, then report the guidance used and the checks that ran or remain unverified.

For feature delivery, bug diagnosis, or release readiness, use the corresponding [task guide](shared/task-execution/README.md) after loading context. These draft guides connect the selected technology modules to a checkable task outcome.

The library is a reference for the agent. Copy or link the selected context into each Flutter project; this repository does not fetch files or configure agents automatically. Backend modules are optional and belong in a project selection only when the Flutter app's API or service integration is part of the work.

## Select workflows

Selections live in `project.yaml`. State management and routing each have one choice. Architecture, networking, storage, authentication, backend, optional UI capabilities, and test stages can contain multiple IDs when they are intentionally composed.

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
  ui: [forms, adaptive-layout, accessibility, localization]
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
  flutter.ui.forms: 0.1.0
  flutter.ui.adaptive-layout: 0.1.0
  flutter.ui.accessibility: 0.1.0
  flutter.ui.localization: 0.1.0
  flutter.testing.closed-testing: 0.1.0
  flutter.deployment.android: 0.1.0
  flutter.deployment.play-store: 0.1.0
```

### Quick selection guide

Start with the project's existing decisions. For a new project, choose only what the product needs. List-based categories can stay empty when no module applies; state management and routing each require one choice in the schema.

| Category | Choose based on |
|---|---|
| State management | Keep the established tool. For a new choice, use GetX for its integrated state and dependency APIs, Riverpod for provider-based state and test overrides, BLoC/Cubit for explicit transitions, or Provider for a small ChangeNotifier layer. Select one primary tool. |
| Architecture | Choose feature-based organization for capability ownership, clean architecture when domain rules need independence from I/O, layered for a few clear technical layers, or MVVM for screen-scoped presentation state. Combine architecture modules only with a documented composition decision. |
| Networking | Use `http` for straightforward requests, Dio for shared configuration/interceptors/cancellation, or Retrofit when typed generated API declarations justify the added setup. Retrofit requires Dio. |
| Routing | Use the project's current router. For a new choice, use GetX routing when it matches the selected GetX app conventions, or GoRouter for declarative paths, redirects, and deep links. Select one router. |
| Storage | Use Shared Preferences for small non-sensitive settings, Secure Storage for credentials, Hive-compatible boxes for local objects, or SQLite for relational queries and transactions. Choose by data shape and sensitivity. |
| Authentication | Select the identity or session modules the app actually uses. Google OAuth is a sign-in provider; Firebase Auth and Supabase Auth manage identity sessions; JWT describes a backend-issued API session. Combine modules only when the integration is deliberate. |
| Backend | Use REST API for the client/server contract, FastAPI when a Python API is part of the project's integration boundary, or Firebase when managed Firebase services fit the product. These modules are optional context for Flutter app work and can describe different layers of one system when that is intentional. |
| UI capabilities | Optionally select `forms` for input/validation/submission, `adaptive-layout` for layout across available space and input modes, `accessibility` for semantic and assistive-technology verification, or `localization` for resources and locale behavior. Combine only those the project uses; omitting `flutter.ui` is valid. Baseline accessibility rules still apply. |
| Testing | Select unit, widget, and integration levels by the behavior being verified. Closed and open testing are tester distribution channels, not automated test levels. |
| Deployment | Select Android or iOS for build targets. Select Play Store when distributing Android builds through Google Play. |

After choosing modules, check their `requires`, `conflicts_with`, and project version pins. When handling a task, load only the selected modules relevant to that change using [the context-loading guide](shared/documentation/agent-context-loading.md).

The canonical machine-readable file is each module's `workflow.yaml`; its `entrypoint` names the human- and agent-readable procedure. IDs are stable even if display names change. `requires` names mandatory module IDs. `conflicts_with` names hard conflicts. Optional `compatible_with` is only advisory and never a complete compatibility matrix.

If two architecture modules are selected, the project must state how they compose. For example, feature-based organization can contain clean-architecture layers. A second state-management or routing module is a conflict unless a deliberate migration or isolated boundary is documented.

## How an agent loads context

Start with the global rules and project configuration, then load just the selected modules relevant to the task. For a GetX feature task, that commonly means the GetX state-management workflow, the chosen architecture, and any selected networking, routing, storage, authentication, and testing modules that the change touches. Do not load Riverpod, BLoC, or Provider simply because they exist in this repository.

See [`shared/documentation/agent-context-loading.md`](shared/documentation/agent-context-loading.md) for the full selection order and conflict behavior. Rules are guidance with different strengths; a conflict between explicit project decisions and a workflow MUST is surfaced for resolution. Repository guidance does not supersede platform or higher-priority instructions.

## Repository map

- `config/` — project configuration schema and a working example.
- `shared/` — engineering rules that apply across the selected Flutter workflows.
- `shared/task-execution/` — draft procedures for feature, bug-fix, and release tasks.
- `workflows/flutter/` — focused, independently versioned Flutter modules.
- `templates/` — starter documents for project records.
- `troubleshooting/` — evidence-based incident records; currently an empty knowledge base.
- `scripts/` — future tooling notes only; there is no generator or workflow engine.
- `VERSION` — release version for this collection. Module versions evolve independently.
- `CHANGELOG.md` — unreleased upgrades and adoption notes.

## Available Flutter modules

- State management: [GetX](workflows/flutter/state-management/getx/workflow.md), [Riverpod](workflows/flutter/state-management/riverpod/workflow.md), [BLoC/Cubit](workflows/flutter/state-management/bloc/workflow.md), [Provider](workflows/flutter/state-management/provider/workflow.md).
- Architecture: [feature-based](workflows/flutter/architecture/feature-based/workflow.md), [clean architecture](workflows/flutter/architecture/clean-architecture/workflow.md), [layered](workflows/flutter/architecture/layered/workflow.md), [MVVM](workflows/flutter/architecture/mvvm/workflow.md).
- Networking: [Dio](workflows/flutter/networking/dio/workflow.md), [http](workflows/flutter/networking/http/workflow.md), [Retrofit](workflows/flutter/networking/retrofit/workflow.md).
- Routing: [GetX](workflows/flutter/routing/getx/workflow.md), [GoRouter](workflows/flutter/routing/go-router/workflow.md).
- Storage: [Hive-compatible](workflows/flutter/storage/hive/workflow.md), [Shared Preferences](workflows/flutter/storage/shared-preferences/workflow.md), [Secure Storage](workflows/flutter/storage/secure-storage/workflow.md), [SQLite](workflows/flutter/storage/sqlite/workflow.md).
- Authentication: [Firebase Auth](workflows/flutter/authentication/firebase-auth/workflow.md), [Google OAuth](workflows/flutter/authentication/google-oauth/workflow.md), [JWT sessions](workflows/flutter/authentication/jwt/workflow.md), [Supabase Auth](workflows/flutter/authentication/supabase-auth/workflow.md).
- Backend: [REST API contracts](workflows/flutter/backend/rest-api/workflow.md), [FastAPI](workflows/flutter/backend/fastapi/workflow.md), [Firebase](workflows/flutter/backend/firebase/workflow.md).
- UI capabilities: [forms and validation](workflows/flutter/ui/forms/workflow.md), [responsive and adaptive layouts](workflows/flutter/ui/adaptive-layout/workflow.md), [accessibility verification](workflows/flutter/ui/accessibility/workflow.md), [localization and locale behavior](workflows/flutter/ui/localization/workflow.md).
- Testing: [unit](workflows/flutter/testing/unit/workflow.md), [widget](workflows/flutter/testing/widget/workflow.md), [integration](workflows/flutter/testing/integration/workflow.md), [closed testing](workflows/flutter/testing/closed-testing/workflow.md), [open testing](workflows/flutter/testing/open-testing/workflow.md).
- Deployment: [Android](workflows/flutter/deployment/android/workflow.md), [iOS](workflows/flutter/deployment/ios/workflow.md), [Google Play](workflows/flutter/deployment/play-store/workflow.md).

## Templates

Start from the relevant file in `templates/`: [project agent context](templates/project/AGENTS.md), [feature brief](templates/feature/feature-brief.md), [bug report](templates/bug-report/bug-report.md), [troubleshooting record](templates/troubleshooting/troubleshooting-record.md), [architecture decision](templates/architecture-decision/adr.md), [code review](templates/code-review/code-review.md), [release checklist](templates/release/release-checklist.md), or [task report](templates/task/task-report.md). The canonical project configuration example is [config/example-project.yaml](config/example-project.yaml).

## Adopt the next upgrade

The [planned 0.2.0 upgrade](CHANGELOG.md) adds four selectable UI modules and shared task guides. The schema remains version 1 with an optional `flutter.ui` list; existing configurations and module pins remain valid under the expanded schema. It is unreleased; `VERSION` identifies the last collection release.

1. Review the new [task guides](shared/task-execution/README.md) and choose one real Flutter task for a pilot.
2. Make the adopted library revision available to the Flutter project through its existing copy or link arrangement. Merge the task-guide pointer from [the project agent template](templates/project/AGENTS.md) into local instructions while preserving project-specific rules. If copying files, include the referenced shared guides and report template and adapt library paths to their actual location in the project.
3. Keep existing workflow selections and pins. Resolve any existing pin mismatch through [context loading](shared/documentation/agent-context-loading.md#check-module-combinations-and-versions); adopting a shared guide is not a reason to rewrite module pins.
   To adopt new UI modules, use this revision's schema, add only the needed `flutter.ui` slugs from [the example](config/example-project.yaml), and optionally pin their module IDs to `0.1.0`. Older library schemas do not recognize the new field, so update the library/schema before adding it.
4. Run the task using its guide and record acceptance evidence in the existing project record or [task report](templates/task/task-report.md). Capture observed guidance gaps using the [pilot procedure](shared/task-execution/README.md#pilot-the-upgrade).

No script copies files or changes a consuming project automatically. The new modules and task guides remain draft until their procedures have evidence from real project use.

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

The intended manual loop is: Flutter project configuration → selected workflow metadata → task-relevant rules and entrypoints → implementation → validation → verified lessons. A loader or validator may be useful after repeated manual use reveals a stable convention worth automating; this repository currently has no automation engine.
