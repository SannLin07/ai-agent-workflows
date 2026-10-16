# Changelog

## Unreleased — planned 0.2.0

### Added

- Four selectable Flutter UI modules: forms and validation, responsive/adaptive layouts, accessibility verification, and localization. Each starts at `0.1.0` with `status: draft`.
- An optional `flutter.ui` selection in the version-1 project schema, example selections/pins, and context-loading instructions for the new category.
- Dated official Flutter references for the new modules and sourced localization package guidance.
- Draft task guides for feature delivery, bug diagnosis and fixes, and release readiness, with a task-based entrypoint and evidence-based completion criteria.
- A task report template that maps acceptance criteria to verification results, records the selected guidance, and identifies missing evidence.
- Manual adoption instructions and a real-task pilot path for the new guides.

### Changed

- Context loading and the project agent template now point to the applicable task guide.
- Feature, bug, and release templates capture the evidence needed by those guides.
- Corrected the library example's unit-testing pin to the existing module version `0.2.0`; consuming project pins are not changed automatically.

### Adoption and maturity

The version-1 configuration schema now accepts optional `flutter.ui` selections. Existing configurations remain valid under the expanded schema; existing module IDs and versions are unchanged. To select the new modules, adopt the updated schema/library before adding `flutter.ui`, since the older schema rejects unknown fields. Follow [the adoption instructions](README.md#adopt-the-next-upgrade) for module selection and shared guides.

The new modules and guides remain draft pending real Flutter project use. Source and documentation checks are not a project pilot. The collection's `VERSION` remains `0.1.0` until a release is made; this entry describes unreleased work.
