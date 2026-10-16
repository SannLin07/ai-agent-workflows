# Release checklist: <version>

Use with the [release readiness guide](../../shared/task-execution/release.md). Attach candidate-specific evidence to required checks; an unchecked item remains unverified.

## Candidate
- Version/build:
- Commit:
- Local changes included in the candidate, if any:
- Artifact location and build environment:
- Platforms and distribution channel:
- Requested action: preparation | distribution
- Selected deployment/release-channel module IDs and versions:
- Current vendor requirements checked, source links, and date:

## Readiness
- [ ] Release notes reviewed
- [ ] Required unit, widget, and integration checks recorded
- [ ] Install, upgrade, permissions, and critical user paths checked
- [ ] Production configuration and secret handling reviewed
- [ ] Crash/error reporting and support path confirmed
- [ ] Store metadata, signing, and platform requirements verified against current official guidance
- [ ] Rollback or recovery plan documented where supported

## Decision and evidence
- Go / no-go:
- Evidence and known limitations:
- Approver:
- Date:
- Missing prerequisites and next actions:
- [Task report](../task/task-report.md) or equivalent acceptance/check evidence:

## Distribution result, when performed
- Artifact and destination:
- Audience / track:
- Observed state and evidence (uploaded, in review, available to testers, publicly available):

## After release
- Monitoring owner and review time:
- [ ] Monitor crashes, errors, and user feedback
- [ ] Record verified incidents and follow-up actions
