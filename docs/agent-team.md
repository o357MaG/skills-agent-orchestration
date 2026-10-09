# Agent team

Mona's Project Pulse dashboard will be built with a four-agent custom team orchestrated from GitHub Copilot CLI in a Codespace.

- Orchestrator — Model: Claude Opus 4.7 (copilot). Responsible for decomposing the task into phases, assigning work to specialist agents, coordinating dependencies, and verifying the final result before reporting back. Source: `.github/agents/orchestrator.agent.md`.
- Planner — Model: Claude Opus 4.7 (copilot). Responsible for researching the repo, reviewing the requirements, identifying dependencies and edge cases, and producing a concrete implementation plan with file ownership and validation steps. Source: `.github/agents/planner.agent.md`.
- Designer — Model: Gemini 3.1 Pro (copilot). Responsible for the Project Pulse user experience: accessibility, hierarchy, layout, interactive clarity, and visual polish for the dashboard. Source: `.github/agents/designer.agent.md`.
- Coder — Model: GPT-5.5 (copilot). Responsible for the implementation work within the Orchestrator's assigned scope, including the static dashboard files and any supporting runnable app configuration. Source: `.github/agents/coder.agent.md`.

The custom agents live under the repository's `.github/agents/` folder, and the team works together through GitHub Copilot CLI to build the Project Pulse dashboard.
