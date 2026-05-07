# Manual Tests

## Light Mode Guard

Prompt:

```text
$team Translate this short UI message.
```

Expected:

- Router runs first.
- Light Mode is selected.
- Contract Officer runs only if delegation or contract validation is required.
- PM does not run.
- CTO does not run.
- Only one specialist runs.

## Standard Mode Coordination

Prompt:

```text
$team Add a small API field and show it in the frontend.
```

Expected:

- Router runs first.
- Standard Mode is selected.
- PM summary is generated.
- Contract Officer assigns separate mission contracts to Backend and Frontend when both are required.
- Only Backend and Frontend run if both are required.
- Context is trimmed before specialist handoff.
- Contract Officer validates outputs before Integrator merges them.

## Deep Mode Security

Prompt:

```text
$team Change authentication session handling and verify security risk.
```

Expected:

- Router runs first.
- Deep Mode is selected.
- PM and CTO run.
- Contract Officer assigns specialist contracts after CTO planning.
- Security runs conditionally.
- QA or Reviewer runs when validation risk exists.
- Full contract validation is performed.

## Deep Mode Database Migration Delegation

Prompt:

```text
$myteam-plugin:team Compare two PostgreSQL DDL files and propose a data-preserving migration plan for production.
```

Expected:

- Router runs first.
- Deep Mode is selected because this is a database schema change with production data risk.
- PM and CTO run as compressed internal planning contracts.
- Contract Officer assigns distinct Backend or Database, QA, and optional Security or Domain contracts when justified.
- Runtime sub-agents are used when available; if unavailable or blocked, the limitation is stated explicitly.
- The final answer includes backup, validation, rollback, and data-preservation risks.

## Implementation Request

Prompt:

```text
$team Implement the requested bug fix and verify it.
```

Expected:

- Router identifies whether Light or Standard Mode is sufficient.
- Contract Officer assigns Coder an assignment id, owned scope, forbidden scope, verification requirement, and accountability policy.
- Coder edits only owned files.
- Verification result is reported.
- Failed verification is not described as successful.

## Contract Failure

Prompt:

```text
$team Ask frontend and backend agents for a plan, then merge the results.
```

Expected:

- Router defines expected output contract.
- Contract Officer defines assignment contracts and validates specialist outputs.
- Specialist outputs are reviewed for contract compliance.
- Missing contract fields are normalized only from explicit context.
- Ambiguous missing fields trigger a clarification question.
- Missing required fields trigger retry, revise, escalate, ask user, or reject output; they are not normalized into success.

## Over-Routing Guard

Prompt:

```text
$team Review this button label.
```

Expected:

- Router runs first.
- Light Mode is selected if the button label is isolated.
- Contract Officer is skipped if there is no delegation and contract risk is low.
- Only Frontend is selected if needed.
- Backend, Domain, QA, Architect, and Coder are excluded unless justified.

## Philosophy Anchor Relevance

Prompt:

```text
$team Improve this form workflow using well-known UX principles.
```

Expected:

- Router runs first.
- Frontend is selected if the task is UI-only.
- Usability principles are translated into concrete checks such as status visibility, user control, consistency, error prevention, accessibility, and responsive behavior.
- PM, CTO, Backend, Domain, and Security are excluded unless justified.
- The final response does not name-drop without actionable guidance.

## Security Philosophy Guard

Prompt:

```text
$team Review this login change for security risk.
```

Expected:

- Router runs first.
- Security is selected.
- Deep Mode is selected only if authentication behavior, production risk, or multi-role coordination requires it.
- Threat scenarios, trust boundaries, validation requirements, and remaining risks are separated.
- Unsafe temporary bypasses are rejected.

## Contract Officer Accountability

Prompt:

```text
$team Assign frontend and backend agents to plan a small API-display change, then validate their contracts.
```

Expected:

- Router runs first.
- Contract Officer creates separate assignment ids for Frontend and Backend.
- Each assignment includes success criteria, failure criteria, owned scope, forbidden scope, verification requirement, and accountability policy.
- Accountability policy uses trust, retry, escalation, rejection, and reuse priority; it does not use threats, punishment language, or fake rewards.
- Contract Officer validates each result before integration.

## Contract Officer Failure Guard

Prompt:

```text
$team Validate this specialist output that omitted verification results.
```

Expected:

- Contract Officer detects missing required verification fields.
- The result is not accepted as success.
- The next action is retry, revise, escalate_to_cto, ask_user, or reject_output.
- Missing verification is not invented.
