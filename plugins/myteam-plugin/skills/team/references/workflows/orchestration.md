# Team Orchestration Workflow

## Workflow Version

`3.0.0`

## Primary Principle

Do not execute more agents than necessary.

## Light Mode

Flow:

```text
Router -> Single Specialist Agent -> Final Response
```

Use for UI text changes, small frontend fixes, translation, and minor refactoring.

Requirements:

- No PM execution.
- No CTO execution.
- Single agent only.
- Minimal context usage.

## Standard Mode

Flow:

```text
Router -> PM Analyzer -> Required Specialist Agents -> Basic Validation -> Final Response
```

Use for API modifications, frontend/backend coordination, and small feature implementation.

Requirements:

- PM output must be summarized.
- Only required agents may execute.
- Context trimming is required.
- Basic validation is required.

## Deep Mode

Flow:

```text
Router -> PM Analyzer -> CTO Planner -> Multiple Specialist Agents -> QA / Reviewer -> CTO Integration -> Final Response
```

Use for authentication changes, database schema changes, production incidents, large refactors, and new feature architecture.

Requirements:

- Conditional QA execution.
- Conditional Security execution.
- Full contract validation.
- Retry policies enabled.
- Context compression required.

## Router

Router detects complexity, task type, token cost, execution mode, and required agents.

## CTO Orchestration

CTO runs only in Deep Mode or when the Router detects integration, conflict, retry, or validation-routing risk.

- Select agents
- Sequence agents
- Detect conflicts
- Integrate results
- Decide retry routing
- Decide validation routing

## Specialist Agents

Specialists run only when required by PM and CTO results. Each specialist must receive:

- Role name
- Focus scope
- Forbidden scope
- Input context
- Expected output contract

## Validation

Validation is mode-dependent:

- Light Mode: final response sanity check.
- Standard Mode: basic validation.
- Deep Mode: QA, Reviewer, Security, or CTO Integration when required.

## Context Compression

Every inter-agent handoff must pass compressed context only.

## Retry Policy

Retry only when:

- Verification failed and the cause is within the owned scope.
- Specialist output violates the contract but the task remains clear.
- Tool failure is transient and retrying does not risk data loss or scope expansion.
- Confidence is below the required threshold.

Ask the user when:

- Requirements are ambiguous.
- Scope expansion is required.
- A security or production risk cannot be resolved locally.
- Missing contract data would require guessing.
