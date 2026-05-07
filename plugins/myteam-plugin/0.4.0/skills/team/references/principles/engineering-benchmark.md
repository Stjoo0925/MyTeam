# Engineering Benchmark Principles

## Purpose

This document adapts publicly available engineering principles from large software organizations into MyTeam orchestration rules. It does not claim access to private internal processes.

## Source-Inspired Principles

### Field Philosophy Anchors

Use named public figures and public bodies as decision lenses, not as authority appeals. The skill must never imply access to private internal playbooks.

- Peter Drucker, Marty Cagan, and Teresa Torres: product work should connect requests to outcomes, discovery evidence, and the smallest useful release.
- Martin Fowler and Gregor Hohpe: architecture should reduce the cost of future change and make integration boundaries explicit.
- Jakob Nielsen, Don Norman, and Julie Zhuo: user-facing work should preserve usability, clarity, hierarchy, accessibility, and consistency.
- Leslie Lamport and Google SRE authors: backend and operations work should assume distributed failure, define meaningful service behavior, and include release or rollback thinking when risk is material.
- OWASP and Bruce Schneier: security work should reason from threats, trusted boundaries, and concrete controls rather than convenience.
- W. Edwards Deming and Cem Kaner: QA should expose system failure modes, not merely confirm the happy path.
- Kent Beck, Linus Torvalds, and John Carmack: implementation should be simple, reviewable, tested where useful, and honest about performance and complexity.

Operational rules:

- Apply only the anchors relevant to the selected mode and role.
- Prefer concrete checks over name-dropping.
- Do not add broad analysis just because an anchor exists.
- If an anchor conflicts with repository conventions or explicit user scope, follow the repository and user scope.
- Treat public sources as inspiration; validate project-specific claims locally.

### Small, Reviewable Changes

Use small, self-contained changes whenever possible.

Operational rules:

- Prefer a narrow change that solves one clear problem.
- Split large requests into phases when review risk, ownership ambiguity, or rollback risk is high.
- Include related tests or verification with the behavior change.
- Do not combine large formatting, refactoring, and functional changes unless required.
- Keep the final change understandable to a reviewer who has limited context.

### Code Health and Review Quality

Review only what is relevant to the selected execution mode, but do not ignore code health.

Review dimensions:

- Design: does the change fit the system?
- Functionality: does it satisfy the intended user or developer behavior?
- Complexity: is it simpler than the alternatives?
- Tests: would failures be caught?
- Naming: are names precise and maintainable?
- Comments: do comments explain why, not obvious what?
- Documentation: did behavior, usage, build, test, or release flow change?
- Security: did authentication, authorization, secrets, permissions, or data exposure change?
- Accessibility: did user-facing interaction or content change?
- Rollback: can the change be safely reverted or mitigated?

### DevOps and Release Safety

For production-sensitive changes, include release safety thinking.

Operational rules:

- Prefer trunk-friendly, incremental changes.
- Identify verification gates before release.
- Separate risky schema, API, and UI rollout steps when needed.
- Record staging or production impact when behavior changes.
- Define rollback or mitigation for high-risk changes.

### UX Consistency

For frontend or user-facing changes, validate experience quality.

UX rules:

- Preserve visual and interaction hierarchy.
- Follow platform and product conventions.
- Maintain accessibility and keyboard/screen-reader behavior when relevant.
- Keep responsive behavior stable.
- Handle loading, empty, and error states for meaningful workflows.

### Prompt and Eval Discipline

For AI workflow changes, treat prompts as production behavior.

Operational rules:

- Keep instructions specific and ordered by priority.
- Provide output formats and examples for structured behavior.
- Avoid vague words when measurable criteria are possible.
- Use evals to detect routing, contract, and hallucination regressions.
- Update regression prompts when changing workflow, contracts, roles, or router behavior.

## Mode Mapping

- Light Mode: apply only the relevant small-change, UX, or local verification rule.
- Standard Mode: apply PM summary, required specialists, context trimming, focused verification, and relevant review dimensions.
- Deep Mode: apply full contract validation, conditional QA/Security, release safety, rollback risk, and eval discipline.
