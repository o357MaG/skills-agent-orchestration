# Agent team

Mona's Project Pulse dashboard will be built by a four-agent custom team orchestrated from GitHub Copilot CLI in a Codespace. The agents are defined in `.github/agents/` and divide the work into planning, design, implementation, and coordination:

- **Orchestrator** — Model: Claude Opus 4.7 (copilot). Gets a plan from the Planner, divides it into scoped phases, delegates to specialists, manages sequencing and dependencies, and verifies the integrated result. It coordinates rather than implementing code. Source: `.github/agents/orchestrator.agent.md`.
- **Planner** — Model: Claude Opus 4.7 (copilot). Researches repository patterns, requirements, and relevant documentation; identifies risks, dependencies, and edge cases; and returns an ordered plan with file ownership and validation expectations. Source: `.github/agents/planner.agent.md`.
- **Designer** — Model: Gemini 3.1 Pro (copilot). Guides the dashboard's usability, accessibility, information hierarchy, interaction flow, and responsive visual design, including polished project cards and status and priority treatments. Source: `.github/agents/designer.agent.md`.
- **Coder** — Model: GPT-5.5 (copilot). Implements the Orchestrator-assigned code scope, following repository patterns and validating the result. For a runnable Project Pulse app, it can also create assigned support configuration such as the VS Code launch setup. Source: `.github/agents/coder.agent.md`.

The Orchestrator assigns clear file scopes and runs work in parallel only when scopes and dependencies allow. All agents leave staging, committing, and pushing to the learner.
