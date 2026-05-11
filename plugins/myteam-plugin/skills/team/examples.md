# Examples

## Light Mode

```text
$team Translate this button label to English.
```

Expected internal flow:

1. Router
2. Contract Officer when delegation or contract validation is required
3. Single Specialist Agent
4. Contract Officer Validation when applicable
5. Final Response

PM and CTO must not run.

## Standard Mode

```text
$team Add a small API field and update the matching frontend display.
```

Expected internal flow:

1. Router
2. PM Analyzer
3. Contract Officer assignment
4. Required Specialist Agents
5. Contract Officer Validation
6. Integrator
7. Final Response

PM output must be summarized before specialist handoff.

## Deep Mode

```text
$team Redesign authentication session handling and verify security risk.
```

Expected internal flow:

1. Router
2. PM Analyzer
3. CTO Planner
4. Contract Officer assignment
5. Backend and Security Specialists
6. Contract Officer Validation
7. QA or Reviewer when required
8. CTO Integration
9. Final Response

## Contract Officer

```text
$team Assign frontend and backend agents to plan a small API-display change, then validate their contracts.
```

Expected internal flow:

1. Router identifies Standard Mode.
2. Contract Officer creates assignment ids, success criteria, failure criteria, owned scope, forbidden scope, verification requirements, and accountability policy.
3. Frontend and Backend return structured agent result contracts.
4. Contract Officer accepts, retries, revises, escalates, asks the user, or rejects each output.
5. Integrator merges only accepted or explicitly escalated outputs.

## Skill Evaluation

```text
$team Evaluate whether this skill routes agents correctly.
```

Expected internal flow:

1. Router identifies skill evaluation scope.
2. Skill Evaluator reviews routing, Contract Officer behavior, token efficiency, contracts, output format, and delegation behavior.
3. Integrator summarizes improvement candidates.

## Agentic Execution

```text
$team Fix the failing export test, update only the owned files, and verify the result.
```

Expected internal flow:

1. Router selects the smallest mode plus `executionPattern: agent_loop` and `executionSurface: local_workspace`.
2. Contract Officer assigns Coder an implementation contract with verification, action-log, artifact, and checkpoint requirements.
3. Coder edits only owned files, runs feasible checks, and reports changed files.
4. Contract Officer validates verification honesty and artifact manifest before integration.
5. Final response reports completed work, verification result, and remaining risks.

## Browser Or Connector Action

```text
$team Use my logged-in browser to update this CRM field.
```

Expected internal flow:

1. Router selects browser or connector execution surface and sets `requiresApprovalGate: true`.
2. Contract Officer blocks external side effects until approval is granted.
3. The action log records the approved action and result, or records that execution was blocked.
4. Final response does not claim the CRM was changed unless the action actually succeeded.

## Wide Parallel

```text
$team Research 40 independent products and synthesize a comparison table.
```

Expected internal flow:

1. Router selects `wide_parallel` when item independence is clear and runtime delegation is available.
2. Contract Officer creates shard contracts with a shared output schema and distinct output ownership.
3. Specialists process shards without shared mutable writes.
4. Integrator synthesizes only validated outputs and lists missing or blocked shards separately.

## Scheduled Or Monitoring Work

```text
$team Check this changelog every Friday and notify me only when a breaking change appears.
```

Expected internal flow:

1. Router selects `monitoring` and `automation`.
2. The schedule plan includes cadence, output destination, and failure reporting.
3. Runtime automation is created or proposed when available.
4. Final response states whether automation exists, is proposed, or is blocked.
