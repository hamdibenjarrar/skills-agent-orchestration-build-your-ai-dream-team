# Project Pulse agent team

This team of custom agents will build Mona's Project Pulse dashboard. Each agent is defined in `.github/agents/`.

| Agent | Model | Responsibility | Definition file |
| --- | --- | --- | --- |
| Orchestrator | Claude Opus 5.5 | Breaks the request into tasks, delegates to the specialists and reports the final result. It coordinates but does not implement. | `.github/agents/orchestrator.agent.md` |
| Planner | Claude Opus 5.5 | Researches the repository and writes the implementation plan with phases, file ownership, dependencies and validation. It does not write code. | `.github/agents/planner.agent.md` |
| Designer | Gemini 3.7 Flash | Owns the user experience: layout, information hierarchy, accessibility and visual design of the dashboard. | `.github/agents/designer.agent.md` |
| Coder | GPT-5.5 | Implements the static app files and the `.vscode/launch.json` launch configuration within the scope it is given. | `.github/agents/coder.agent.md` |

## How the team works together

1. The Orchestrator receives the Project Pulse request from Copilot CLI.
2. The Orchestrator asks the Planner for a plan saved in `docs/project-pulse-plan.md`.
3. Following the plan, the Orchestrator asks the Designer for the visual and accessibility decisions.
4. The Orchestrator hands the plan and the design guidance to the Coder, who builds `app/index.html`, `app/styles.css`, `app/project-data.json` and `.vscode/launch.json`.
5. The Orchestrator validates the result and writes the final handoff.
