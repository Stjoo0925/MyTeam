# MyTeam

This repository manages a personal MyTeam Orchestrator plugin for Codex.

MyTeam behaves like a team lead. It does not jump directly into implementation. It first analyzes the request from a PM perspective, then selects only the specialist roles that are actually needed.

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
        agents/
          openai.yaml
        references/
          routing.json
          agents/
            pm.md
            frontend.md
            backend.md
            coder.md
            architect.md
            domain.md
            qa.md
            skill_evaluator.md
```

## Usage

Invoke the skill in Codex like this:

```text
$team Analyze this requirement from the MyTeam perspective.
```

The only direct command is `$team`. PM, Frontend, Backend, Architect, Domain, QA, Coder, and Skill Evaluator are internal roles selected by `$team` only when needed.

## Operating Principles

- Always run PM analysis first.
- Use the PM result to identify MVP scope, risks, hidden requirements, and operational constraints.
- Select only the specialist roles that are necessary.
- Use the Coder role only when code changes are required.
- The Coder role edits only the assigned files or modules and runs feasible verification commands.
- For code review, impact analysis, architectural bottlenecks, and technical debt analysis, check whether `code-review-graph` tools are available.
- Before the final response, verify that the result does not exceed the user's requested scope.

## Maintenance Rules

- Main orchestrator instructions live in `plugins/myteam-plugin/skills/team/SKILL.md`.
- Role-specific guidance lives in `plugins/myteam-plugin/skills/team/references/agents/`.
- Routing keywords live in `plugins/myteam-plugin/skills/team/references/routing.json`.
- Plugin registration metadata lives in `plugins/myteam-plugin/.codex-plugin/plugin.json`.
- Codex UI marketplace registration lives in `.agents/plugins/marketplace.json`.

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
