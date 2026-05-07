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
- Do not retry ambiguous requirements. Ask the user.
- Do not retry security-sensitive changes with unsafe temporary bypasses.
- Escalate to CTO only in Deep Mode or when failure creates integration risk.
