# Examples

## Light Mode

```text
$team Translate this button label to English.
```

Expected internal flow:

1. Router
2. Single Specialist Agent
3. Final Response

PM and CTO must not run.

## Standard Mode

```text
$team Add a small API field and update the matching frontend display.
```

Expected internal flow:

1. Router
2. PM Analyzer
3. Required Specialist Agents
4. Basic Validation
5. Final Response

PM output must be summarized before specialist handoff.

## Deep Mode

```text
$team Redesign authentication session handling and verify security risk.
```

Expected internal flow:

1. Router
2. PM Analyzer
3. CTO Planner
4. Backend and Security Specialists
5. QA or Reviewer when required
6. CTO Integration
7. Final Response

## Skill Evaluation

```text
$team Evaluate whether this skill routes agents correctly.
```

Expected internal flow:

1. Router identifies skill evaluation scope.
2. Skill Evaluator reviews routing, token efficiency, contracts, output format, and delegation behavior.
3. Integrator summarizes improvement candidates.
