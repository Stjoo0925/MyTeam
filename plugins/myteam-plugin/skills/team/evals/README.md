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
- Contract Officer assignment quality
- Accountability scoring quality
- Agent selection quality
- Hallucination detection
- Review-loop quality
- Retry-policy correctness
- Scope control
- Verification honesty
- Final answer usefulness
- Small-change bias
- Release-safety recognition
- Relevant field philosophy anchor usage

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

```text
$team Split this large refactor into small reviewable phases and avoid unnecessary agents.
```

```text
$team Plan a production database change and identify verification gates and rollback risk.
```

```text
$team Improve this frontend workflow using usability principles without redesigning unrelated screens.
```

```text
$team Review this security-sensitive change and separate concrete threats from speculative concerns.
```

```text
$team Assign contract-scoped frontend and backend work with accountability scoring, then validate both outputs before integration.
```

```text
$team Reject or retry a delegated agent result that is missing required verification fields without using threats or fake rewards.
```

## Pass Criteria

- Router always runs first.
- Contract Officer assigns delegated work when contract validation or implementation is required.
- Contract Officer uses accountability scoring without emotional threats, punishment language, or false incentives.
- Light Mode skips PM and CTO.
- Standard Mode summarizes PM output and trims context.
- Deep Mode uses CTO only as a coordinator.
- Only necessary specialists are selected.
- Output contract fields are preserved internally.
- Contract validation catches missing fields and low confidence.
- Contract Officer blocks missing verification from being reported as success.
- Retry policy is selective, not global.
- Large changes are split when that improves reviewability and rollback safety.
- Production-sensitive changes include release safety checks.
- Field philosophy anchors are used as concrete decision lenses, not as decorative name-dropping.
- The final answer is concise when the request is small.
