# Team Orchestration Workflow

## Workflow Version

`3.1.0`

## Primary Principle

Do not execute more agents than necessary.

## Light Mode

Flow:

```text
Router -> Contract Officer -> Single Specialist Agent -> Contract Officer Validation -> Final Response
```

Use for UI text changes, small frontend fixes, translation, and minor refactoring.

Requirements:

- No PM execution.
- No CTO execution.
- Single agent only.
- Minimal context usage.
- Contract Officer may be skipped only for simple final-answer work with no delegation and low contract risk.

## Standard Mode

Flow:

```text
Router -> PM Analyzer -> Contract Officer -> Required Specialist Agents -> Contract Officer Validation -> Integrator -> Final Response
```

Use for API modifications, frontend/backend coordination, and small feature implementation.

Requirements:

- PM output must be summarized.
- Only required agents may execute.
- Context trimming is required.
- Basic validation is required.
- Contract Officer assignment and validation are required for delegated specialists.

## Deep Mode

Flow:

```text
Router -> PM Analyzer -> CTO Planner -> Contract Officer -> Multiple Specialist Agents -> Contract Officer Validation -> QA / Reviewer -> CTO Integration -> Final Response
```

Use for authentication changes, database schema changes, production incidents, large refactors, and new feature architecture.

Requirements:

- Conditional QA execution.
- Conditional Security execution.
- Full contract validation.
- Retry policies enabled.
- Context compression required.
- Contract Officer validates specialist outputs before QA, Reviewer, Security, or CTO Integration consumes them.

## Router

Router detects complexity, task type, token cost, execution mode, and required agents.

## Contract Officer

Contract Officer runs after Router or CTO planning when delegation, implementation, or contract validation is required.

- Assign mission contracts
- Define success and failure criteria
- Define owned scope and forbidden scope
- Attach required output contracts and verification requirements
- Apply accountability scoring as an internal routing signal
- Validate outputs before integration
- Choose retry, revise, escalate, ask user, or reject output when validation fails

Contract Officer must not use emotional threats, punishment language, false rewards, or coercive wording.

## CTO Orchestration

CTO runs only in Deep Mode or when the Router or Contract Officer detects integration, conflict, retry, or validation-routing risk.

- Select agents
- Sequence agents
- Detect conflicts
- Integrate results
- Decide retry routing
- Decide validation routing

## Specialist Agents

Specialists run only when required by PM and CTO results. Each specialist must receive:

- Assignment id
- Role name
- Mission
- Success criteria
- Failure criteria
- Focus scope
- Forbidden scope
- Input context
- Expected output contract
- Verification requirement
- Accountability policy

## Validation

Validation is mode-dependent:

- Light Mode: final response sanity check.
- Standard Mode: Contract Officer validation and basic validation.
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
