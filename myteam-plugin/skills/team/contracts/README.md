# Contracts

Contracts define stable input and output shapes for MyTeam orchestration.

Use these contracts for all inter-agent handoffs.

- `router-decision.schema.json`: Router execution mode and agent selection result.
- `agent-result.schema.json`: Specialist, QA, Security, Coder, and Integrator result handoff.
- `team-orchestration.yaml`: End-to-end orchestration contract.

Contract rules:

- Required fields must be present in internal orchestration state.
- Final user responses may be shorter, but must not contradict the contract.
- Missing required fields must be resolved through CTO Review.
- If required fields cannot be resolved from explicit context, ask the user instead of guessing.
- Agents must not exchange raw conversational outputs.
- Full chat history transfer is forbidden.
