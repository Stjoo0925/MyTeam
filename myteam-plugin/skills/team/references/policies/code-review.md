# Code Review Policy

## Version

`1.0.0`

## Goal

Keep code health from declining while avoiding unnecessary review overhead.

## Mode-Based Review

### Light Mode

Check only the directly relevant dimensions:

- Does the small change satisfy the request?
- Is the change scoped to one clear concern?
- Is verification feasible?
- Does the final response stay concise?

### Standard Mode

Check:

- Design fit
- Functionality
- Complexity
- Focused tests or verification
- Documentation impact
- Cross-agent contract consistency

### Deep Mode

Check:

- Architecture fit
- Security and privacy risk
- Concurrency or data consistency risk
- Migration and rollback risk
- Release sequencing
- Full contract validation
- QA or Reviewer output when required

## Review Rules

- Prefer small self-contained changes.
- Reject speculative abstractions unless they remove proven complexity.
- Do not mix unrelated refactors with behavior changes.
- Require documentation updates when user-facing, operational, build, test, or release behavior changes.
- Treat missing verification honestly.
