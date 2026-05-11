# MyTeam

This repository manages a personal MyTeam Orchestrator plugin for Codex.

MyTeam behaves like a token-efficient execution orchestrator. It routes every request first, selects Light, Standard, or Deep mode, classifies whether the task needs direct response, agent loop, wide parallel processing, scheduling, or monitoring, uses a Contract Officer to assign and validate delegated work when needed, executes only the required runtime agents, exchanges structured contracts, and validates results conditionally.

For actionable requests, MyTeam is expected to plan, act with available tools, observe results, verify the outcome, track artifacts, and keep checkpoints when the work may continue later.

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
            agentic-execution.md
            code-review.md
            context-compression.md
            release-safety.md
            retry-escalation.md
          principles/
            engineering-benchmark.md
          workflows/
            orchestration.md
            registry.json
            agents/
              router.md
              contract_officer.md
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

The direct command is `$team`; plugin invocation such as `$myteam-plugin:team` has the same orchestration intent. 길잡이 (`router`) always runs first. For non-trivial analysis, multi-file comparison, database migration planning, implementation, verification, review, impact analysis, browser or connector work, scheduled follow-up, and wide parallel processing, MyTeam delegates to the smallest sufficient set of runtime sub-agents when they are available. 약속지기 (`contract_officer`), 그림잡이 (`pm`), 판짜기장 (`cto`), 화면마술사 (`frontend`), 엔진장인 (`backend`), 구조연금술사 (`architect`), 현장박사 (`domain`), 빈틈탐정 (`qa`), 문지기 (`security`), 뚝딱장인 (`coder`), 매듭장이 (`integrator`), and 거울감별사 (`skill_evaluator`) are internal roles selected only when needed.

## Operating Principles

- Always run 길잡이 (`router`) first.
- Classify execution pattern and execution surface for actionable work.
- Use a plan-act-observe-verify loop for implementation, browser, connector, shell, artifact, and automation work.
- Require approval before authenticated browser, connector, destructive, purchase, posting, messaging, or cross-workspace actions.
- Maintain action logs, artifact manifests, and checkpoints when relevant.
- Use Wide Parallel only for many independent items that can be sharded and synthesized safely.
- Route delayed, recurring, follow-up, and monitoring requests to automation when available.
- Use 약속지기 (`contract_officer`) to assign and validate delegated work when delegation, implementation, or contract validation is required.
- Do not treat token efficiency as permission to skip eligible sub-agent delegation for non-trivial `$team` work.
- Use Light Mode for simple requests with one specialist and no PM or CTO.
- Use Standard Mode for medium-complexity work with PM summary, required specialists, context trimming, and basic validation.
- Use Deep Mode only for high-risk or large-scale work with CTO coordination, conditional QA or Security, full contract validation, and retry policies.
- Select only the specialist roles that are necessary.
- Exchange structured contracts instead of raw conversational outputs.
- Use accountability scoring as an internal routing signal; do not use emotional threats, punishment language, or fake rewards.
- Compress context before every inter-agent handoff.
- Use the 뚝딱장인 (`coder`) role only when code changes are required.
- The 뚝딱장인 (`coder`) role edits only the assigned files or modules and runs feasible verification commands.
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
- Agentic execution, context compression, release safety, code review, and retry policies live in `plugins/myteam-plugin/skills/team/references/policies/`.
- Engineering benchmark principles live in `plugins/myteam-plugin/skills/team/references/principles/`.
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
C:\Users\{userName}\.codex\plugins\cache\personal-plugins\myteam-plugin\0.6.0
```

The marketplace file is managed relative to the cache root:

```text
C:\Users\{userName}\.codex\plugins\cache\personal-plugins\.agents\plugins\marketplace.json
```

In `marketplace.json`, the plugin path should use `./plugins/myteam-plugin` relative to the marketplace source root.
