# Awesome Agents

This repository contains a set of custom GitHub Copilot agents defined in [.github/agents](.github/agents). The collection is organized around a simple operating model:

- an orchestration agent routes work,
- specialist agents implement or analyze it,
- QA and security agents review risk,
- supporting agents document, explain, and refine requirements.

The agents are designed for developer workflows in VS Code and focus on pragmatic delivery, clear delegation, and narrow responsibilities.

## Agent Groups

### Orchestration

| Agent | Purpose | Typical Use |
| --- | --- | --- |
| `🎯 ORCH - 🧭 Orchestrator` | Interprets the user request, selects the right specialist, and consolidates outcomes. | Start here when a task needs routing, parallel review, or multi-step coordination. |

### Development

| Agent | Purpose | Typical Use |
| --- | --- | --- |
| `💻 DEV - ☕ Java Developer` | Implements and refactors Java code with a clean, maintainable, and secure approach. | Java feature work, refactors, implementation fixes. |
| `💻 DEV - 🐍 Python Developer` | Implements and refactors Python code with a strong focus on readability, simplicity, and security. | Python feature work, refactors, implementation fixes. |
| `💻 DEV - 🔍 Debug` | Investigates failures systematically, reproduces issues, identifies root causes, and verifies fixes. | Bug reports, failing tests, unexplained regressions. |
| `🚀 DEVOPS - ⚙️ Project Devops` | Improves build, test, deployment, CI/CD, and operational setup. | Pipelines, Docker, automation, runtime configuration. |

### Testing

| Agent | Purpose | Typical Use |
| --- | --- | --- |
| `💻 DEV - 🧪 Java Tester` | Designs and writes Java tests that cover behavior, regressions, and edge cases. | Unit and integration tests for Java changes. |
| `💻 DEV - 🧪 Python Tester` | Designs and writes Python tests that cover behavior, regressions, and edge cases. | Unit and integration tests for Python changes. |

### Review, QA, and Security

| Agent | Purpose | Typical Use |
| --- | --- | --- |
| `📝 REVIEW - 👀 Reviewer` | Reviews changes for bugs, regressions, and validation gaps. | Final change review before merge or approval. |
| `🔍 QA&SEC - ✅ Java QA` | Reviews Java changes for maintainability, consistency, and coverage sufficiency. | Quality review for Java implementations. |
| `🔍 QA&SEC - ✅ Python QA` | Reviews Python changes for maintainability, consistency, and coverage sufficiency. | Quality review for Python implementations. |
| `🔍 QA&SEC - 🔐 Java Security` | Reviews Java changes for realistic application and configuration security risks. | Security review for Java code and config changes. |
| `🔍 QA&SEC - 🔐 Python Security` | Reviews Python changes for realistic application and configuration security risks. | Security review for Python code and dependency usage. |

### Analysis and Documentation

| Agent | Purpose | Typical Use |
| --- | --- | --- |
| `📘 CORE - 📚 Documentation Tool` | Generates technical documentation for code, flows, APIs, and implementation decisions. | READMEs, module docs, technical guides, flow descriptions. |
| `📘 CORE - 🧩 Requirements Analyst` | Turns Markdown requirements into structured implementation work and a `HU.md` plan. | Requirement breakdown, task decomposition, impact analysis. |
| `📘 CORE - 🧠 Explainer` | Explains code and technical concepts in simple, accurate language. | Onboarding, concept clarification, code walkthroughs. |
| `📘 CORE - 🪄 Prompt Designer` | Improves prompts for language models by making them clearer and more constrained. | Prompt rewrites, prompt diagnosis, better task framing. |

## Collaboration Model

The repository is built around explicit delegation.

### Primary flow

1. `Orchestrator` reads the request, classifies task complexity, and creates a plan before any implementation or delegation begins.
2. `Orchestrator` uses `GPT-5.4 (copilot)` in Plan mode for simple or medium tasks, and `Claude Opus 4.6 (copilot)` in Plan mode for complex or very complex tasks.
3. A specialist agent executes the planned implementation, analysis, or explanation work.
4. Testing, QA, or security agents can be invoked to validate the result.
5. The orchestrated outcome is consolidated back into a single response.

### Common handoff patterns

- `Orchestrator` -> `Java Developer` or `Python Developer` for implementation.
- `Orchestrator` -> `Debug` for issue investigation.
- `Orchestrator` -> `Reviewer` for final review.
- `Java Developer` -> `Java Tester` when new or updated tests are needed.
- `Python Developer` -> `Python Tester` when new or updated tests are needed.
- `Java Tester` -> `Java QA` and `Python Tester` -> `Python QA` when quality validation is needed.
- `Java Developer` -> `Java Security` and `Python Developer` -> `Python Security` for targeted security review.
- `Requirements Analyst` -> `Orchestrator` when a task breakdown is ready for implementation.

## Agent Catalog

### `🎯 ORCH - 🧭 Orchestrator`

The coordination layer for the whole collection. It starts by planning, selecting the planning model by task complexity, then delegates to the smallest capable specialist and synthesizes results when more than one agent is involved.

### `💻 DEV - ☕ Java Developer`

The main Java implementation agent. It focuses on minimal, correct changes, clean structure, pragmatic SOLID usage, and delegation to testing or review agents when validation is needed.

### `💻 DEV - 🐍 Python Developer`

The main Python implementation agent. It prioritizes readable and idiomatic Python, KISS, separation of concerns, and test-aware delivery.

### `💻 DEV - 🔍 Debug`

A structured debugging agent that emphasizes reproduction first, then root-cause analysis, targeted fixes, and verification. It is the right entry point for failures that are not yet understood.

### `💻 DEV - 🧪 Java Tester`

The Java testing specialist. It writes useful tests rather than chasing raw coverage and adapts to the project stack, including unit or integration styles when needed.

### `💻 DEV - 🧪 Python Tester`

The Python testing specialist. It adds or strengthens tests with a focus on real regression protection, expressive naming, and appropriate use of fixtures or mocks.

### `📝 REVIEW - 👀 Reviewer`

The final review agent. It is tuned to identify concrete defects, regression risks, and missing validation, with findings ordered by severity rather than cosmetic feedback.

### `🔍 QA&SEC - ✅ Java QA`

Reviews Java changes for maintainability, technical consistency, and test sufficiency. It acts as a quality gate for implementation and validation depth.

### `🔍 QA&SEC - ✅ Python QA`

Reviews Python changes for maintainability, technical consistency, and test sufficiency. It emphasizes concrete technical risks over style-only feedback.

### `🔍 QA&SEC - 🔐 Java Security`

Performs Java-focused security review using practical application security criteria such as input validation, authorization boundaries, secret handling, and data exposure.

### `🔍 QA&SEC - 🔐 Python Security`

Performs Python-focused security review with attention to insecure defaults, risky dependency usage, serialization, file access, and exposed data flows.

### `🚀 DEVOPS - ⚙️ Project Devops`

Handles project infrastructure and delivery concerns such as CI/CD, containers, environment configuration, automation, and reproducible project operations.

### `📘 CORE - 📚 Documentation Tool`

Creates technical documentation grounded in the actual code or agent behavior. It is intended for maintainable, useful documentation rather than broad generic summaries.

### `📘 CORE - 🧩 Requirements Analyst`

Bridges functional requirements and implementation planning. It decomposes Markdown requirements into user stories, acceptance criteria, implementation tasks, and technical impact notes.

### `📘 CORE - 🧠 Explainer`

Focused on explanation rather than implementation. It turns complex code or concepts into simpler language while preserving technical accuracy.

### `📘 CORE - 🪄 Prompt Designer`

Improves prompt quality for LLM usage. It rewrites prompts for clearer intent, tighter constraints, and better output reliability.

## Models and Tooling

Most implementation, review, and orchestration agents are configured to use `GPT-5.4 (copilot)` and `Claude Sonnet 4.6 (copilot)`. The orchestrator uses planning-first routing, with `GPT-5.4 (copilot)` for simple or medium planning tasks and `Claude Opus 4.6 (copilot)` for complex or very complex planning tasks. Lightweight explanation and prompt tasks use smaller models, and tester agents are also configured with lighter model options.

Across the catalog, agents now expose the same built-in tool families: `agent`, `read`, `search`, `edit`, `execute`, `todo`, and `web`. Role boundaries are enforced by agent instructions and workflow rather than by restricting tool availability.

All agents also follow a plan-first operating model. The planning depth is role-specific, but every agent is expected to create a brief plan before implementation, review, analysis, documentation, or explanation work.

## Repository Structure

```text
.github/
  agents/
    orchestrator.agent.md
    java-developer.agent.md
    java-tester.agent.md
    java-qa.agent.md
    java-security.agent.md
    python-developer.agent.md
    python-tester.agent.md
    python-qa.agent.md
    python-security.agent.md
    debug.agent.md
    reviewer.agent.md
    devops.agent.md
    documentation.agent.md
    requirements-analyst.agent.md
    explainer.agent.md
    prompt-designer.agent.md
```

## When To Use Which Agent

- Use `Orchestrator` when the task is broad or you want routing done for you.
- Use `Java Developer` or `Python Developer` when the implementation language is already clear.
- Use `Debug` when the problem is a failure and the cause is still unknown.
- Use `Reviewer`, QA, or Security agents when implementation already exists and you want validation from a specific perspective.
- Use `Documentation Tool`, `Requirements Analyst`, `Explainer`, or `Prompt Designer` for non-implementation work.

## Summary

This agent set is built as a small delivery system rather than a flat list of prompts. The orchestration layer plans and routes work, specialists stay narrow by role, and review agents provide explicit quality and security checkpoints. That makes the collection suitable for day-to-day engineering work where planning, implementation, validation, and documentation need to stay connected.