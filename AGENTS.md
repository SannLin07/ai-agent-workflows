# Maintaining this workflow library

For a task in this repository, read `README.md` and the relevant workflow or shared rule before editing it. Keep each rule in one canonical location and link to it from dependent workflows.

When changing a workflow, preserve its stable `id`, update `version` according to `CONTRIBUTING.md`, and keep `workflow.yaml` aligned with its entrypoint. Record verified package or platform facts with an authoritative source and date. Mark unpiloted guidance as `draft`; do not add hypothetical troubleshooting incidents.

For a project implementation task that uses this library, follow `shared/documentation/agent-context-loading.md` to load only the selected workflows that apply to the task.
