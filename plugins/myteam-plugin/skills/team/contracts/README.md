# Contracts

Contracts define stable input and output shapes for MyTeam orchestration.

Use these contracts for all inter-agent handoffs.

- `router-decision.schema.json`: Router execution mode and agent selection result.
- `agent-result.schema.json`: Specialist, QA, Security, Coder, and Integrator result handoff.
- `team-orchestration.yaml`: End-to-end orchestration, Contract Officer assignment, accountability, validation, and final output contract.

Contract rules:

- Required fields must be present in internal orchestration state.
- Final user responses may be shorter, but must not contradict the contract.
- Missing required fields must be resolved through the smallest valid path: Router correction, the owning agent, or CTO Review only when escalation is justified by mode or integration risk.
- If required fields cannot be resolved from explicit context, ask the user instead of guessing.
- Agents must not exchange raw conversational outputs.
- Full chat history transfer is forbidden.
- Router decisions must include execution strength, delegation eligibility, skipped agents, and overuse guard details.
- Router decisions must state whether Contract Officer assignment or validation is required.
- Strong execution means required capabilities must be used decisively, including actual runtime delegation when eligible, but every extra agent must have a distinct reason and ownership boundary.
- For `$team` or `$myteam-plugin:team`, sub-agent delegation is required when the task is non-trivial, has distinct ownership or verification value, and the runtime provides suitable explorer or worker agents.
- Sub-agent delegation is forbidden when it duplicates work, expands scope, or replaces a simple single-agent path.
- Agent results must include assignment id, owned scope, forbidden scope, verification status, contract compliance status, accountability score delta, and Contract Officer decision.
- Accountability scoring is an internal routing signal. Emotional threats, punishment language, and false rewards are forbidden.
