# Copilot instructions for this repository

## Repository purpose

This repository is the “Agent Orchestration: Build Your AI Dream Team” exercise. The goal is to use GitHub Copilot CLI and custom agents to orchestrate creation of a small Project Pulse dashboard for Mona’s team.

The actual product work is intentionally split across a few files and specialist roles:

- `.github/agents/` contains the custom agent definitions used by the exercise (`Orchestrator`, `Planner`, `Designer`, `Coder`).
- `.github/project-pulse-brief.md` defines the application requirements.
- `app/` contains the static dashboard (`index.html`, `styles.css`, `project-data.json`).
- `.vscode/launch.json` is the preview configuration for the dashboard.
- `docs/` stores learner-facing write-ups such as the agent team summary, implementation plan, and handoff notes.

## Build, test, and validation commands

There is no application framework or package manifest in this repository, so there is no npm/yarn or unit-test harness to run. The repo’s validation target is the exercise checker:

- `bash scripts/validate-exercise.sh`

For focused validation of generated app files, use direct JSON checks when relevant:

- `python3 -m json.tool app/project-data.json`
- `python3 -m json.tool .vscode/launch.json`

When previewing the dashboard, use the VS Code configuration named “Run Project Pulse Dashboard” from `.vscode/launch.json` so it serves the `app/` directory and opens `index.html` directly.

## High-level architecture

This repo is a static front-end exercise rather than a multi-page app or service. The important architecture is:

1. Requirements live in `.github/project-pulse-brief.md`.
2. The multi-agent workflow is defined in `.github/agents/*.agent.md` and should be used as orchestration instructions, not implementation detail.
3. The actual dashboard is assembled from three files in `app/`:
   - `app/index.html` renders the page structure and project cards.
   - `app/styles.css` provides the dashboard styling and visual polish.
   - `app/project-data.json` provides the data model as a top-level `projects` array.
4. `.vscode/launch.json` makes the app easy to open in VS Code without exposing a server directory listing.
5. `docs/` should contain the exercise outputs and handoff notes the learner creates during the task flow.

## Key conventions specific to this repository

- Use the orchestrator workflow: Planner creates the plan, Designer handles the experience, Coder handles implementation, and the Orchestrator coordinates the phases and verifies the result.
- Keep learner git operations in the terminal flow; do not add automation that stages, commits, or pushes changes for the user.
- Preserve the Project Pulse data contract in `app/project-data.json`:
  - top-level `projects` array
  - each project object includes `name`, `owner`, `status`, `recentActivity`, and `priority`
- Keep `.vscode/launch.json` strict JSON with no comments.
- For the dashboard app, prefer deterministic hooks such as `.dashboard` and `.project-card` in the CSS so the generated UI is easy to validate.
- Use polished static dashboard patterns rather than bare HTML: visible cards, status badges, readable spacing, rounded corners, and box shadows.
- Start the app preview from `${workspaceFolder}/app` and open `index.html`, not the folder listing.
- Treat `.github/agents/` as the source of workflow expectations; do not treat it as generic documentation to ignore.

## Practical workflow for future sessions

When working in this repo:

- Read `.github/project-pulse-brief.md` before implementation.
- Check the agent definitions in `.github/agents/` when the task depends on multi-agent orchestration.
- Prefer the repo’s existing validation flow (`bash scripts/validate-exercise.sh`) over inventing new checks.
- Update `docs/` with planning and handoff content only when the exercise requires it.
- Keep the implementation focused on the static dashboard files and the launch configuration, rather than introducing framework tooling or unrelated services.
