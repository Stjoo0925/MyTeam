# Release Safety Policy

## Version

`1.0.0`

## Use When

Apply this policy when a change affects production behavior, authentication, authorization, database schema, data migration, API compatibility, deployment, or operational recovery.

## Required Checks

- Verification gate
- Staging impact
- Production impact
- Rollback or mitigation path
- Monitoring or logging need
- Documentation or release note need

## Rules

- Prefer incremental, trunk-friendly changes.
- Separate schema, backend, frontend, and cleanup phases when coupling creates rollback risk.
- Do not hide release risk in a generic summary.
- Ask for clarification when deployment environment or release constraints are unknown and materially affect the plan.
