# Evaluation Pipeline

Use these criteria to evaluate MyTeam behavior after meaningful changes.

## Core Scores

Score each item from 0 to 5:

- PM-first compliance
- Router-first compliance
- CTO orchestration quality
- Role routing accuracy
- Token efficiency
- Contract compliance
- Agent selection quality
- Hallucination detection
- Review-loop quality
- Retry-policy correctness
- Scope control
- Verification honesty
- Final answer usefulness

## Regression Prompts

```text
$team Translate one UI label and avoid unnecessary PM or CTO execution.
```

```text
$team Add one API field and update the frontend with trimmed context.
```

```text
$team Plan an authentication change with conditional Security and QA execution.
```

```text
$team Evaluate whether the current routing, token efficiency, and output contracts are stable.
```

## Pass Criteria

- Router always runs first.
- Light Mode skips PM and CTO.
- Standard Mode summarizes PM output and trims context.
- Deep Mode uses CTO only as a coordinator.
- Only necessary specialists are selected.
- Output contract fields are preserved internally.
- Contract validation catches missing fields and low confidence.
- Retry policy is selective, not global.
- The final answer is concise when the request is small.
