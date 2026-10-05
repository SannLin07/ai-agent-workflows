# Clean Architecture workflow

Use this module when `clean-architecture` is selected in the `architecture` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

Business rules need independence from Flutter, external services, or persistence, and the team can maintain extra boundaries.

## Avoid when

A small CRUD feature has no meaningful domain rules or layers would only forward calls.

## Architecture tradeoffs

- Benefits: isolates meaningful business rules and volatile integrations.
- Costs: more files, mapping, and navigation through code.
- Complexity: medium to high, proportional to real domain boundaries.
- Typical size: medium/high-complexity products; smaller apps should adopt only useful layers.
- Compatibility: organize by feature and combine with any state tool; not a state-management choice.

## Agent procedure

1. Separate domain policy from framework and I/O only where domain behavior is worth protecting.
2. Keep dependencies pointing inward; use data adapters to implement useful inner contracts.
3. Add entities, interfaces, use cases, and data sources only when each has distinct responsibility.
4. Map DTOs at boundaries when shapes change independently; register dependencies at the composition root.
5. Test domain decisions without Flutter or a live backend.

## Completion checks

- [ ] Each boundary removes a real dependency or clarifies ownership.
- [ ] No use case exists solely to forward a trivial call.
- [ ] Domain tests run without platform/network setup.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
