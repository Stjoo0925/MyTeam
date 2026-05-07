# MyTeam

This repository manages a personal MyTeam Orchestrator plugin for Codex.

MyTeam behaves like a token-efficient team orchestrator. It routes every request first, selects Light, Standard, or Deep mode, executes only the required agents, exchanges structured contracts, and validates results conditionally.

## Structure

```text
.agents/
  plugins/
    marketplace.json
plugins/
  myteam-plugin/
    .codex-plugin/
      plugin.json
    assets/
      myteam.svg
    skills/
      team/
        SKILL.md
        version.json
        changelog.md
        examples.md
        tests.md
        agents/
          openai.yaml
        contracts/
          README.md
          agent-result.schema.json
          router-decision.schema.json
          team-orchestration.yaml
        evals/
          README.md
        references/
          routing.json
          policies/
            context-compression.md
            retry-escalation.md
          workflows/
            orchestration.md
            registry.json
          agents/
            router.md
            pm.md
            cto.md
            frontend.md
            backend.md
            coder.md
            architect.md
            domain.md
            qa.md
            security.md
            integrator.md
            skill_evaluator.md
```

## Usage

Invoke the skill in Codex like this:

```text
$team Analyze this requirement from the MyTeam perspective.
```

The only direct command is `$team`. Router always runs first. PM, CTO, Frontend, Backend, Architect, Domain, QA, Security, Coder, Integrator, and Skill Evaluator are internal roles selected by `$team` only when needed.

## Operating Principles

- Always run Router first.
- Use Light Mode for simple requests with one specialist and no PM or CTO.
- Use Standard Mode for medium-complexity work with PM summary, required specialists, context trimming, and basic validation.
- Use Deep Mode only for high-risk or large-scale work with CTO coordination, conditional QA or Security, full contract validation, and retry policies.
- Select only the specialist roles that are necessary.
- Exchange structured contracts instead of raw conversational outputs.
- Compress context before every inter-agent handoff.
- Use the Coder role only when code changes are required.
- The Coder role edits only the assigned files or modules and runs feasible verification commands.
- Preserve the team orchestration contract for non-trivial tasks.
- For code review, impact analysis, architectural bottlenecks, and technical debt analysis, check whether `code-review-graph` tools are available.
- Before the final response, verify that the result does not exceed the user's requested scope.

## Maintenance Rules

- Main orchestrator instructions live in `plugins/myteam-plugin/skills/team/SKILL.md`.
- Skill, role, workflow, prompt, contract, dependency, and deployment versions live in `plugins/myteam-plugin/skills/team/version.json`.
- Workflow registry lives in `plugins/myteam-plugin/skills/team/references/workflows/registry.json`.
- Change history lives in `plugins/myteam-plugin/skills/team/changelog.md`.
- Role-specific guidance lives in `plugins/myteam-plugin/skills/team/references/agents/`.
- Workflow guidance lives in `plugins/myteam-plugin/skills/team/references/workflows/`.
- Input/output contracts live in `plugins/myteam-plugin/skills/team/contracts/`.
- Context compression and retry policies live in `plugins/myteam-plugin/skills/team/references/policies/`.
- Evaluation prompts and scoring rules live in `plugins/myteam-plugin/skills/team/evals/`.
- Routing keywords live in `plugins/myteam-plugin/skills/team/references/routing.json`.
- Plugin registration metadata lives in `plugins/myteam-plugin/.codex-plugin/plugin.json`.
- Codex UI marketplace registration lives in `.agents/plugins/marketplace.json`.

## Versioning Policy

MyTeam follows Semantic Versioning for skill and contract changes.

- Major: role responsibility changes, orchestration structure changes that break existing behavior, or breaking contract changes.
- Minor: new role capability, new workflow stage, new tool dependency, or backward-compatible contract expansion.
- Patch: prompt wording changes, output stability improvements, bug fixes, or documentation clarification.

## Install Location

An example personal plugin cache location recognized by the Codex app:

```text
C:\Users\yusco\.codex\plugins\cache\personal-plugins\myteam-plugin
```

The marketplace file is managed relative to the cache root:

```text
C:\Users\yusco\.codex\plugins\cache\personal-plugins\.agents\plugins\marketplace.json
```

In `marketplace.json`, the plugin path should use `./plugins/myteam-plugin` relative to the cache root.
