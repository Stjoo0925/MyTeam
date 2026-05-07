# Retry and Escalation Policy

## Version

`1.0.0`

## Retry Conditions

- Contract validation failure
- Missing required outputs
- Low confidence score
- Failed verification with a clear cause inside owned scope
- Transient tool failure

## Default Retry Limit

```json
{
  "maxRetries": 2,
  "escalateTo": "cto"
}
```

## Rules

- Retries must be selective, not global.
- Retry only the failed agent or failed validation stage.
- Do not rerun PM, CTO, or all specialists for a single malformed specialist result.
- Do not retry a delegated agent that was only assigned duplicate confidence checking. Exclude the output and continue with verified local evidence.
- Retry or wait for a delegated agent only when its distinct owned scope is required for the next decision.
- If a delegated agent times out and its result is not required, report it as unavailable in validation limits and do not merge it.
- Do not retry ambiguous requirements. Ask the user.
- Do not retry security-sensitive changes with unsafe temporary bypasses.
- Escalate to CTO only in Deep Mode or when failure creates integration risk.
