# Team Orchestration Workflow

## Workflow Version

`3.1.0`

## Primary Principle

Do not execute more agents than necessary, but execute the Router-selected delegated agents when runtime sub-agents are available.

## Light Mode

Flow:

```text
Router -> Contract Officer -> Single Specialist Agent -> Contract Officer Validation -> Final Response
```

Use for UI text changes, small frontend fixes, translation, and minor refactoring.

Requirements:

- No PM execution.
- No CTO execution.
- Single specialist only.
- Delegate to one specialist when the task is non-trivial and runtime sub-agents are available.
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
- Use actual delegated specialists when the task has distinct backend, frontend, domain, QA, security, or implementation ownership.

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
- Use actual delegated specialists for non-trivial database schema changes, production incidents, authentication or authorization changes, large refactors, and new feature architecture when runtime sub-agents are available.
- Contract Officer validates specialist outputs before QA, Reviewer, Security, or CTO Integration consumes them.

## Router

길잡이 (`router`) detects complexity, task type, token cost, execution mode, and required agents.

## Contract Officer

약속지기 (`contract_officer`) runs after 길잡이 (`router`) or 판짜기장 (`cto`) planning when delegation, implementation, or contract validation is required.

- Assign mission contracts
- Define success and failure criteria
- Define owned scope and forbidden scope
- Attach required output contracts and verification requirements
- Apply accountability scoring as an internal routing signal
- Validate outputs before integration
- Choose retry, revise, escalate, ask user, or reject output when validation fails

Contract Officer must not use emotional threats, punishment language, false rewards, or coercive wording.

## CTO Orchestration

판짜기장 (`cto`) runs only in Deep Mode or when 길잡이 (`router`) or 약속지기 (`contract_officer`) detects integration, conflict, retry, or validation-routing risk.

- Select agents
- Sequence agents
- Detect conflicts
- Integrate results
- Decide retry routing
- Decide validation routing

## Specialist Agents

Specialists run only when required by PM and CTO results. Each specialist must receive:

Use these display names in human-facing labels while preserving internal contract keys:

- 화면마술사 (`frontend`)
- 엔진장인 (`backend`)
- 구조연금술사 (`architect`)
- 현장박사 (`domain`)
- 빈틈탐정 (`qa`)
- 문지기 (`security`)
- 뚝딱장인 (`coder`)
- 매듭장이 (`integrator`)
- 거울감별사 (`skill_evaluator`)

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
