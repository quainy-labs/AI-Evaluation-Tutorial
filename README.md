# AI Evaluation

This repository contains practical learning material for evaluating AI systems, with
a special focus on LLM applications, RAG systems, agents, copilots, and other modern
AI product workflows.

The goal is to help builders move beyond vague quality checks and create evaluation
systems that are repeatable, inspectable, and connected to real product decisions.

## What Is Inside

| File | Purpose |
| --- | --- |
| `AI_EVALUATION_TUTORIAL.md` | A comprehensive practical guide to AI evaluation concepts, workflows, risks, metrics, reporting, and production monitoring. |
| `LLM_OUTPUT_EVALUATION_PYTHON_EXAMPLE.md` | A hands-on Markdown walkthrough with a runnable Python example for evaluating LLM outputs across multiple phases. |
| `AI_EVALUATION_ENGINEER_ROADMAP.md` | A staged roadmap for becoming an AI evaluation engineer, including skills, projects, tools, and interview readiness. |

## Recommended Learning Path

1. Start with `AI_EVALUATION_TUTORIAL.md` to understand the full evaluation lifecycle.
2. Read `LLM_OUTPUT_EVALUATION_PYTHON_EXAMPLE.md` to see how the ideas become a practical evaluation harness.
3. Use `AI_EVALUATION_ENGINEER_ROADMAP.md` to plan deeper skill building and portfolio projects.
4. Adapt the Python example to your own use case by replacing the sample customer-support cases with your product's real tasks, risks, and success criteria.
5. Turn the evaluation into a regression suite that can be rerun whenever prompts, models, tools, retrieval data, or policies change.

## Core Evaluation Loop

Use this loop for most AI evaluation projects:

1. Define the decision question.
2. Map users, tasks, risks, and constraints.
3. Build representative test cases.
4. Choose metrics and rubrics.
5. Run baseline evaluations.
6. Analyze failures and tradeoffs.
7. Improve the system.
8. Rerun regression evaluations.
9. Document the decision.
10. Monitor production behavior.

## Practical Focus

The material emphasizes:

- Product-specific evaluation instead of generic benchmark chasing.
- Risk-aware test design.
- Deterministic checks where possible.
- Human or model-graded rubrics where judgment is needed.
- Slice-based analysis to avoid misleading averages.
- Clear release gates and decision records.
- Continuous evaluation after launch.

## Example Use Cases

You can adapt the evaluation patterns here for:

- Customer-support assistants
- RAG knowledge assistants
- AI tutors
- Coding copilots
- Research assistants
- AI agents using tools
- Classifiers and extractors
- Safety and policy review systems

## Repository Notes

This is currently a Markdown-first learning repository. The Python example is embedded
inside the practical walkthrough so learners can read the explanation and code together.

The local `QUAINY_CONTEXT.md` file is intentionally ignored by Git because it is project
context rather than public tutorial content.
