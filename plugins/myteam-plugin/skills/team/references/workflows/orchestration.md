# Team Orchestration Workflow

## Workflow Version

`3.2.0`

## Primary Principle

Do not execute more agents than necessary, but execute the Router-selected delegated agents when runtime sub-agents are available.

For actionable requests, MyTeam must execute through a plan-act-observe-verify loop instead of stopping at advice. If execution is blocked by scope, approval, missing tools, or policy, the final response must say what was blocked and what state is ready to resume.

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

## Agentic Execution Pattern

Attach this pattern to any mode when the task requires action, browser or connector use, file changes, automation, generated artifacts, or resumable work.

Flow:

```text
Router -> Execution Pattern Selection -> Contract Officer when needed -> Plan -> Act -> Observe -> Verify -> Artifact / Checkpoint -> Final Response
```

Requirements:

- Router classifies `executionPattern` and `executionSurface`.
- The team lead keeps a current goal, plan, observation list, verification method, and stopping condition.
- Contract Officer assigns approval, artifact, and checkpoint requirements when delegation or validation is required.
- Tool-using work keeps an action-log summary.
- Deliverable-producing work keeps an artifact manifest.
- Long-running, interrupted, scheduled, or resumable work keeps a checkpoint.

## Wide Parallel Pattern

Use for many independent repeated items.

Flow:

```text
Router -> PM when needed -> Contract Officer -> Sharded Specialists -> Validation -> Integrator Synthesis -> Final Response
```

Requirements:

- Do not use for sequential workflows.
- State the item source, item count, independence reason, shard policy, and synthesis schema.
- Each shard receives a narrow context and writes only to its owned output scope.
- Timed-out, unavailable, malformed, or rejected shard outputs are excluded from verified synthesis.

## Browser, Connector, And Automation Surfaces

- `local_browser` and `cloud_browser` require approval before interaction with logged-in accounts, forms, postings, messages, bookings, purchases, or sensitive data.
- `external_connector` requires approval before sending or changing external records unless the user explicitly requested that exact action.
- `automation` is used for delayed, recurring, follow-up, or monitoring requests when the runtime provides automation support.
- If a requested surface is unavailable, mark the action blocked and continue only with safe preparation or planning.

## Router

길잡이 (`router`) detects complexity, task type, token cost, execution mode, execution pattern, execution surface, required agents, approval gates, artifact needs, state needs, and scheduling needs.

## Contract Officer

약속지기 (`contract_officer`) runs after 길잡이 (`router`) or 판짜기장 (`cto`) planning when delegation, implementation, or contract validation is required.

- Assign mission contracts
- Define success and failure criteria
- Define owned scope and forbidden scope
- Attach required output contracts and verification requirements
- Attach execution surface, approval, action-log, artifact, and checkpoint requirements when relevant
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

Action logs, artifact manifests, and checkpoints should be summarized before handoff. Do not pass raw browser transcripts, full command output, or full conversation history unless a selected specialist explicitly needs a narrow excerpt.

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
