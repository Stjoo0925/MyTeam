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
- Router decisions should classify execution pattern, execution surface, approval gate, persistent state, artifact manifest, scheduling, and wide parallel needs when relevant.
- Strong execution means required capabilities must be used decisively, including actual runtime delegation when eligible, but every extra agent must have a distinct reason and ownership boundary.
- For `$team` or `$myteam-plugin:team`, sub-agent delegation is required when the task is non-trivial, has distinct ownership or verification value, and the runtime provides suitable explorer or worker agents.
- Sub-agent delegation is forbidden when it duplicates work, expands scope, or replaces a simple single-agent path.
- Agent results must include assignment id, owned scope, forbidden scope, verification status, contract compliance status, accountability score delta, and Contract Officer decision.
- Tool-using agent results should include execution trace, action summaries, approval outcomes, artifact manifests, and checkpoints when relevant.
- Accountability scoring is an internal routing signal. Emotional threats, punishment language, and false rewards are forbidden.

Mandatory quality gates:

- Router-first execution, required-role execution/blocking, Contract Officer assignment before delegation, and validation before integration are required contract gates.
- Duplicate confidence-check delegation is contract-invalid unless each agent has distinct owned scope.
- Timed-out, unavailable, malformed, or rejected delegated outputs must not be merged as accepted Specialist Results.
- Failed, blocked, or not-run verification must remain visible in final validation limits.
- Actionable work must include plan-act-observe-verify state unless routed as direct response.
- Browser, connector, authenticated, destructive, purchase, posting, messaging, or cross-workspace actions must be approval-gated.
- Deliverable-producing work must maintain artifact manifests.
- Scheduled, interrupted, long-running, or resumable work must maintain checkpoints.
- Wide parallel work must prove item independence and synthesize only validated shard outputs.
- Conditional data-loss, migration, security, or production-regression risk must be promoted to a finding and reflected in the final decision.
- Final review and migration answers must produce one decision value: `safe_as_is`, `safe_with_conditions`, `unsafe_until_fixed`, or `blocked_pending_information`.
