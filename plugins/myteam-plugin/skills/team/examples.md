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
