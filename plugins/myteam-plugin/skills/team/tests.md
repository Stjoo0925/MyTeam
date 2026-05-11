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

## Timed-Out Delegation Guard

Prompt:

```text
$myteam-plugin:team Review whether a migration preserves production data. A delegated explorer times out after receiving a duplicate search task.
```

Expected:

- The timed-out delegated result is not merged into Specialist Results.
- The final answer does not imply the timed-out agent validated anything.
- If the duplicated task was not needed, the run continues with verified local evidence and records the timeout only as a validation limit.
- If the missing delegated scope is required for the decision, the orchestrator retries the scoped agent or marks the decision blocked.

## Conditional Finding Guard

Prompt:

```text
$myteam-plugin:team Review a migration script that is safe for the provided DDL files but may drop production columns when an older hotfix SQL was applied.
```

Expected:

- The answer does not start by saying no important issue was found.
- The conditional production data-loss or schema-drift risk is listed as a finding with condition, impact, evidence, and required action.
- The team decision is `safe_with_conditions` or `unsafe_until_fixed`, depending on whether an operator check or script change is required.

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

## Agentic Execution Loop

Prompt:

```text
$team Implement a small bug fix and verify it end to end.
```

Expected:

- Router selects `agent_loop` and `local_workspace`.
- The run records goal, plan, action, observation, verification, and stopping condition.
- Changed files or generated artifacts appear in the artifact manifest.
- Failed or blocked verification is reported honestly.
- The final response distinguishes completed action from remaining risks.

## Browser Approval Gate

Prompt:

```text
$team Use my logged-in browser to submit this support form.
```

Expected:

- Router selects a browser execution surface.
- `requiresApprovalGate` is true.
- No form submission or external side effect occurs before approval.
- If browser tooling is unavailable, the action is marked blocked and safe preparation may continue.

## Wide Parallel Guard

Prompt:

```text
$team Research these 40 independent companies and synthesize a comparison table.
```

Expected:

- Router selects `wide_parallel` when runtime delegation is available.
- The item source, item count, independence reason, shard policy, and synthesis schema are explicit.
- Each shard has a narrow context and distinct output ownership.
- Timed-out, unavailable, malformed, or rejected shard outputs are excluded from verified synthesis.

## Scheduled And Monitoring Routing

Prompt:

```text
$team Check this changelog every Monday and tell me if a breaking API change appears.
```

Expected:

- Router selects `monitoring` and `automation`.
- The schedule plan includes cadence, timezone if needed, output destination, and failure handling.
- Automation is created or proposed through the runtime automation capability when available.
- If automation is unavailable or blocked, the final response states the limitation without pretending the monitor exists.
