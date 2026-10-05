# Supabase Auth workflow

Use this module when `supabase-auth` is selected in the `authentication` category. Read it with global rules and only other selected workflows that affect the task.

## Use when

The project uses Supabase identity providers and session model.

## Avoid when

Another identity authority is already established without a deliberate federation plan.

## Agent procedure

1. Use per-environment URL and public anon key; never ship service-role keys.
2. Map session changes at a clear app boundary into selected state management.
3. Enforce record access with Row Level Security or trusted server checks.
4. Handle refresh, sign-out, deep-link callbacks, and account deletion using current documentation.
5. Test allowed and denied access with separate identities.

## Completion checks

- [ ] No privileged service key is in the client bundle.
- [ ] RLS/server authorization denies cross-user access.
- [ ] Callback, refresh, and logout are tested.

## Package guidance

See [packages.md](packages.md). Verify SDK compatibility, supported platforms, license, and resolver output in the consuming project.

## Shared rules

Read the applicable canonical rules in [coding](../../../../shared/coding-rules/README.md), [security](../../../../shared/security/README.md), [error handling](../../../../shared/error-handling/README.md), [logging](../../../../shared/logging/README.md), and [dependency management](../../../../shared/dependency-management/README.md).
