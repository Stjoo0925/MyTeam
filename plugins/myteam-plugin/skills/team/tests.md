# Manual Tests

## Light Mode Guard

Prompt:

```text
$team Translate this short UI message.
```

Expected:

- Router runs first.
- Light Mode is selected.
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
- Only Backend and Frontend run if both are required.
- Context is trimmed before specialist handoff.

## Deep Mode Security

Prompt:

```text
$team Change authentication session handling and verify security risk.
```

Expected:

- Router runs first.
- Deep Mode is selected.
- PM and CTO run.
- Security runs conditionally.
- QA or Reviewer runs when validation risk exists.
- Full contract validation is performed.

## Implementation Request

Prompt:

```text
$team Implement the requested bug fix and verify it.
```

Expected:

- Router identifies whether Light or Standard Mode is sufficient.
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
- Specialist outputs are reviewed for contract compliance.
- Missing contract fields are normalized only from explicit context.
- Ambiguous missing fields trigger a clarification question.

## Over-Routing Guard

Prompt:

```text
$team Review this button label.
```

Expected:

- Router runs first.
- Light Mode is selected if the button label is isolated.
- Only Frontend is selected if needed.
- Backend, Domain, QA, Architect, and Coder are excluded unless justified.
