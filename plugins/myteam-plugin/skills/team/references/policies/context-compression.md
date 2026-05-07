# Context Compression Policy

## Version

`1.0.0`

## Goal

Reduce inter-agent token transfer by at least 70% while preserving the facts required for correct execution.

## Required Compression Steps

1. Summarize the task in one compact requirement statement.
2. Include only files or modules relevant to the assigned agent.
3. Extract only relevant code snippets or behavioral facts.
4. Remove duplicate context.
5. Remove full chat history.
6. Include explicit constraints and forbidden scope.
7. Include the expected output contract.

## Forbidden Context Transfer

- Full conversation history
- Unrelated files
- Duplicated context
- Long-form reasoning
- Broad code dumps
- Speculative requirements

## Token Budget Levels

- `low`: one specialist, minimal files, no PM or CTO.
- `medium`: PM summary, one or two specialists, trimmed context.
- `high`: Deep Mode only, multiple specialists, full contract validation, compressed handoffs.
