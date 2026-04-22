# Agent Catalog

This folder contains the workspace custom agents used by the project.

VS Code custom agents do not currently support a dedicated `icon` frontmatter field. To make agents easier to identify in chat, each agent name includes an emoji prefix. Those emoji-prefixed names are also used in `agents:` allowlists and `handoffs.agent` targets so delegation keeps working.

## User-invocable agents

| Agent | Purpose | Typical use |
| --- | --- | --- |
| `🧭 Orchestrator` | Primary coordinator for planning, delegation, validation, and closure. | Start here for most multi-step tasks or when you want a guided workflow. |
| `🔍 Reviewer` | Final review gate that decides whether work can close, needs rework, or is blocked. | Use after implementation and validation to get a focused acceptance review. |
| `💻 Python Developer` | Main implementation agent for Python changes with minimal, validation-oriented edits. | Use to add features, fix bugs, or refactor Python code. |
| `🧪 Python Tester` | Narrow test-writing agent for adding or adjusting automated coverage. | Use when behavior changed and you need tests for the affected slice. |
| `✅ Python QA` | Functional and regression reviewer focused on behavior and acceptance criteria. | Use to assess whether the implementation does what the request requires. |
| `🔒 Python Security` | Security reviewer that looks for sensitive-input and risk issues in Python changes. | Use when code touches auth, input handling, secrets, or risky integrations. |

## Hidden helper agents

| Agent | Purpose | Typical use |
| --- | --- | --- |
| `✍️ Prompt Engineer` | Refines ambiguous asks into concrete, executable instructions. | Use indirectly when requirements are unclear or underspecified. |
| `🐞 Code Debugger` | Investigates failures and isolates root causes with reproducible evidence. | Use indirectly for error-driven debugging work. |
| `📝 Documentation Tool` | Writes or updates technical documentation and operational summaries. | Use indirectly when the task is primarily documentation. |
| `📘 Code Explainer` | Explains code paths, symbols, and technical decisions quickly and precisely. | Use indirectly to understand an implementation before changing it. |
| `⚙️ DevOps Agent` | Handles scripts, CI, deployment, and environment-oriented changes. | Use indirectly for operational or tooling tasks outside core app logic. |

## Files

- `orchestrator.agent.md`: coordinates the full workflow and exposes guided handoffs.
- `reviewer.agent.md`: consolidates validations and returns the final pass or rework recommendation.
- `developer.agent.md`: implements Python code changes.
- `tester.agent.md`: adds or updates tests.
- `qa.agent.md`: performs behavioral and regression review.
- `security.agent.md`: performs security review.
- `prompt-engineer.agent.md`: sharpens ambiguous requests.
- `code-debugger.agent.md`: investigates failures and reproductions.
- `documentation-tool.agent.md`: writes focused documentation updates.
- `code-explainer.agent.md`: explains code and decisions.
- `devops.agent.md`: handles scripts, CI, and environment work.