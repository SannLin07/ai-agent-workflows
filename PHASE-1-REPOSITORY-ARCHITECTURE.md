# Flutter Engineering System: Repository Architecture

**Status:** Phase 1 proposal  
**Purpose:** Define the repository structure and the boundary between its reusable engineering materials before building the contents.

## 1. Goal

Create one GitHub repository that acts as a personal, reusable engineering playbook for future Flutter projects. It should help both the developer and AI coding agents follow consistent standards, while keeping project-specific code and decisions in each application repository.

The system has six kinds of material:

1. **Rules** set standards and constraints.
2. **Skills** guide an agent through a specific kind of task.
3. **Documents** explain concepts and provide reference material for people.
4. **Workflows** define the order of work and its checkpoints.
5. **Templates** provide starting files and project structures.
6. **Knowledge** records experience, troubleshooting, and decisions.

These categories are complementary. A workflow can link to a skill, which must follow relevant rules and may use a template; knowledge records what was learned while carrying it out.

## 2. Proposed repository tree

```text
flutter-engineering-system/
├── README.md
├── AGENTS.md
├── CHANGELOG.md
├── docs/
│   ├── architecture/
│   │   ├── architecture-overview.md
│   │   ├── folder-structure.md
│   │   └── dependency-direction.md
│   ├── state-management/
│   │   ├── decision-guide.md
│   │   ├── getx.md
│   │   ├── riverpod.md
│   │   └── bloc.md
│   ├── development/
│   │   ├── api-integration.md
│   │   └── authentication.md
│   ├── testing/
│   │   ├── testing-strategy.md
│   │   └── release-testing.md
│   ├── git/
│   │   └── git-workflow.md
│   └── career/
│       ├── career-roadmap.md
│       └── current-goals.md
├── rules/
│   ├── architecture.md
│   ├── dart-and-flutter.md
│   ├── naming.md
│   ├── state-management.md
│   ├── errors-and-logging.md
│   ├── api-and-authentication.md
│   ├── security.md
│   ├── git.md
│   └── testing.md
├── skills/
│   ├── define-requirements/
│   │   └── SKILL.md
│   ├── plan-flutter-project/
│   │   └── SKILL.md
│   ├── implement-feature/
│   │   └── SKILL.md
│   ├── integrate-api/
│   │   └── SKILL.md
│   ├── write-tests/
│   │   └── SKILL.md
│   ├── debug-flutter-issue/
│   │   └── SKILL.md
│   ├── review-changes/
│   │   └── SKILL.md
│   └── prepare-release/
│       └── SKILL.md
├── workflows/
│   ├── project-start.md
│   ├── requirements-and-planning.md
│   ├── feature-development.md
│   ├── code-review.md
│   ├── testing-and-release.md
│   ├── troubleshooting.md
│   └── project-completion.md
├── templates/
│   ├── flutter-project/
│   ├── requirements/
│   ├── planning/
│   ├── issue/
│   ├── pull-request/
│   ├── adr/
│   └── checklists/
├── knowledge/
│   ├── README.md
│   ├── lessons-learned.md
│   ├── common-solutions.md
│   ├── troubleshooting/
│   │   ├── android/
│   │   ├── ios/
│   │   ├── linux/
│   │   ├── gradle/
│   │   ├── firebase/
│   │   └── packages/
│   ├── decisions/
│   └── career/
│       └── learning-log.md
└── .github/
    ├── ISSUE_TEMPLATE/
    └── PULL_REQUEST_TEMPLATE.md
```

Empty directories are placeholders for later phases; they do not need to be committed until they contain useful files. The Flutter project template can be kept small at first and expanded when the playbook has been tried on a real app.

## 3. What belongs in each category

| Category | Put here | Keep out |
|---|---|---|
| `rules/` | Stable defaults that projects and agents should follow: architecture boundaries, naming, error handling, security, Git, and testing expectations. | Step-by-step task procedures, background tutorials, or one-off project exceptions. |
| `skills/` | Reusable, task-focused agent instructions: inputs to inspect, steps to take, relevant rules to read, expected output, and completion checks. | General policy duplicated from rules, or broad project lifecycle checklists. |
| `docs/` | Explanations, comparisons, reference guides, and career direction for a human reader. | Mandatory policy phrased only in prose, or an operational checklist that belongs in a workflow. |
| `workflows/` | End-to-end sequences, decision gates, handoffs, and checklists such as project kickoff, feature development, review, release, and completion. | Detailed implementation tutorials or project-specific status updates. |
| `templates/` | Blank or example starting points that should be copied and adapted: app skeleton, requirement brief, plan, issue, PR, ADR, and checklists. | Completed project records or canonical rules that can drift from `rules/`. |
| `knowledge/` | Verified lessons, troubleshooting records, common fixes, and decision history from real work. | Unverified guesses, secrets, or rules that have not been deliberately reviewed and promoted. |

### Placement test

When adding material, ask:

- Does it say **what must or must not happen**? Put it in `rules/`.
- Does it tell an agent **how to perform one bounded task**? Put it in `skills/`.
- Does it explain **why something works or compare options**? Put it in `docs/`.
- Does it sequence **multiple tasks or define a project checkpoint**? Put it in `workflows/`.
- Is it a reusable **blank/example to start from**? Put it in `templates/`.
- Was it learned from a **real issue, fix, or decision**? Put it in `knowledge/`.

If an item seems to fit two places, keep one canonical version and link to it from the other. Do not copy the same rule into every skill or template.

## 4. Repository responsibilities

### `README.md`

The front door for a person: explain the purpose, who the system is for, how to navigate the six categories, how to apply the playbook to a Flutter project, and how to contribute a lesson.

### `AGENTS.md`

The short entry point for AI agents working in this repository. It should tell an agent to read the relevant rules and workflow, look up a matching skill when available, treat `knowledge/` as evidence rather than policy, and avoid changing project-specific standards without recording the reason. Keep it an index and bootstrap instruction, not a duplicate of every rule.

### `.github/`

GitHub-specific issue and pull-request forms. These should point to the corresponding templates or workflows where possible, so GitHub does not become a second source of truth.

### `docs/career/` and `knowledge/career/`

Career roadmap and current goals are intentional human-facing planning documents. The learning log records progress and lessons over time. Since the repository is intended to become a portfolio, only put information here that is appropriate to share publicly; keep private notes outside the public repository.

## 5. How a future Flutter project uses the system

The engineering system remains its own repository and does not contain a production application. At project start, use `workflows/project-start.md` and `templates/flutter-project/` to create a project-specific baseline. Copy or adapt the small set of rules, agent entry instructions, and templates the app needs; link to the full playbook for broader reference.

Each app keeps its own decisions and context. Project-specific choices can override a default only when the app records the reason, scope, and owner in its own documentation. A generally useful improvement is proposed back to this system after it has been validated.

The first adoption method should be straightforward copying from a tagged version of the playbook. Automation to sync or generate project files belongs in a later phase, after the manual workflow has proved what should be shared.

## 6. Agent reading and work sequence

For a task in a future project, an agent should:

1. Read that project's `AGENTS.md` and context first.
2. Read the applicable system rules and the relevant workflow.
3. Load a matching skill if the task has one.
4. Check relevant knowledge entries for known pitfalls, treating them as guidance to verify against the current project.
5. Do the work and use the workflow's completion checks.
6. Record a new reusable lesson in the app or propose it for `knowledge/` after confirming it is useful beyond that app.

Rules define the constraints; workflows define the order; skills define task execution. An agent should not infer that a troubleshooting note is a mandatory rule.

## 7. Keeping the system maintainable

- Give each rule and guide one canonical home; link rather than duplicate.
- Keep rules few, concrete, and reviewable. Prefer defaults with a stated reason over absolute claims that do not fit every app.
- Give troubleshooting entries a consistent shape: **symptom, environment/version, cause, fix, verification, prevention**.
- Record durable architecture choices as ADRs using `templates/adr/`; keep project ADRs in the app repository and system-wide ADRs in `knowledge/decisions/`.
- Review a lesson before turning it into a rule. A project-specific fix is not automatically a universal standard.
- Version meaningful changes and use `CHANGELOG.md` to explain changes that affect projects adopting the system.
- Review the playbook after using it on real projects; remove steps that do not help and add material for repeated problems.

## 8. Suggested first release scope

Build this in small increments rather than filling every folder at once:

1. Write `README.md` and the short root `AGENTS.md`.
2. Add a compact first set of rules: architecture, Dart/Flutter, security, errors, Git, and testing.
3. Add project-start, feature-development, code-review, and project-completion workflows.
4. Add only the skills needed for the first real project.
5. Create requirement, PR, ADR, and checklist templates.
6. Add knowledge entries when real troubleshooting or decisions produce them.
7. Build and refine `templates/flutter-project/` after the first project reveals what should be reusable.

This order creates a usable baseline early while leaving state-management comparisons, platform runbooks, release automation, and additional agent roles to grow from actual needs.

## 9. Decisions established by this proposal

- The repository is a playbook and template source, not an application repository.
- Rules, Skills, Documents, Workflows, Templates, and Knowledge have separate purposes and canonical locations.
- AI-agent instructions point to the canonical rules instead of embedding duplicate copies.
- Project-specific context and decisions stay with each application.
- The first distribution method is a versioned manual copy; synchronization automation is deferred until the format has been used.
- Public career materials must be shareable and contain no private notes or secrets.
