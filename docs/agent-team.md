# Agent team

For Mona's Project Pulse dashboard, I will use a four-agent custom team orchestrated through GitHub Copilot CLI in a Codespace.

- Orchestrator — Model: Claude Opus 4.7 (copilot). Responsible for breaking the work into phases, delegating to specialist agents, coordinating dependencies, and verifying that all pieces fit together before reporting progress. Definition: `.github/agents/orchestrator.agent.md`.
- Planner — Model: Claude Opus 4.7 (copilot). Responsible for researching the repository, checking relevant docs and dependencies, identifying edge cases, and producing an ordered implementation plan with file assignments and validation expectations. Definition: `.github/agents/planner.agent.md`.
- Designer — Model: Gemini 3.1 Pro (copilot). Responsible for user experience, accessibility, information hierarchy, responsive layout, and the visual polish of the Project Pulse dashboard. Definition: `.github/agents/designer.agent.md`.
- Coder — Model: GPT-5.5 (copilot). Responsible for implementing code changes, fixing bugs, and writing the project logic within the scope delegated by the Orchestrator, including any assigned runnable app support. Definition: `.github/agents/coder.agent.md`.

All four custom agent definitions live under the repository's `.github/agents/` folder and are managed through GitHub Copilot CLI in the Codespace to coordinate the dashboard build.
