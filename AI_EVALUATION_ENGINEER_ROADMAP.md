# AI Evaluation Engineer Roadmap

## Purpose

This roadmap helps learners become practical AI evaluation engineers: people who can
design, run, interpret, and improve evaluations for AI systems before and after launch.

An AI evaluation engineer sits between product judgment, software engineering, data
science, ML systems, risk review, and user research. The role is not just about running
benchmarks. It is about building evidence that helps teams decide whether an AI system
is useful, reliable, safe, and ready for a specific context.

## What An AI Evaluation Engineer Does

An AI evaluation engineer:

- Defines evaluation goals from product and safety decisions.
- Builds representative datasets and test suites.
- Designs rubrics for human and model-based grading.
- Implements automated evaluation pipelines.
- Evaluates LLMs, RAG systems, agents, classifiers, and multimodal systems.
- Finds failures, explains root causes, and recommends improvements.
- Tracks regressions across prompts, models, tools, and data changes.
- Creates reports that product, engineering, policy, and leadership teams can trust.
- Monitors production behavior after launch.

The core mindset is:

> Do not ask whether the model is impressive. Ask whether the system is fit for the
> users, tasks, risks, and decisions that matter.

## Roadmap Overview

| Stage | Focus | Outcome |
| --- | --- | --- |
| 1 | Foundations | Understand AI systems, LLM behavior, metrics, and evaluation thinking. |
| 2 | Python and data skills | Build datasets, scripts, reports, and automated checks. |
| 3 | LLM evaluation | Evaluate output quality, factuality, safety, and instruction following. |
| 4 | RAG and agent evaluation | Evaluate retrieval, grounding, tool use, planning, and traces. |
| 5 | Human and model grading | Build rubrics, review workflows, and judge calibration processes. |
| 6 | Production evaluation | Monitor drift, regressions, incidents, latency, cost, and user feedback. |
| 7 | Portfolio and job readiness | Ship evaluation projects that demonstrate practical judgment. |

## Stage 1: Evaluation Foundations

### Learn

- What AI evaluation means.
- Difference between model evaluation and system evaluation.
- Offline vs online evaluation.
- Deterministic vs judgment-based evaluation.
- Accuracy, precision, recall, F1, calibration, robustness, fairness, latency, and cost.
- Failure severity and risk levels.
- Why averages can hide serious failures.

### Practice

- Read 20 real AI product examples and list what could go wrong.
- For each product, write the decision question an evaluation should answer.
- Create a simple risk map with accuracy, safety, privacy, fairness, cost, and UX risks.

### Deliverable

Create an evaluation brief for one AI product:

```markdown
# Evaluation Brief

## System

## Decision

## Users

## Tasks

## Risks

## Success Criteria

## Release Gate
```

### You Are Ready To Move On When

- You can explain why "the model got 90%" may still be unsafe.
- You can turn a vague product goal into measurable evaluation questions.
- You can define severe failures before seeing results.

## Stage 2: Python And Data Skills

### Learn

- Python basics for files, JSON, CSV, dictionaries, and functions.
- `pandas` for dataset inspection and aggregation.
- `pytest` for regression tests.
- Basic statistics: mean, median, percentiles, confidence intervals.
- Data cleaning and schema validation.
- Reproducible scripts and versioned outputs.

### Practice

- Load a CSV of test cases.
- Validate required fields.
- Score outputs with simple rules.
- Aggregate pass rate by category.
- Write results to JSON and Markdown.

### Mini Project

Build a command-line evaluator:

```text
python evaluate.py --cases cases.csv --outputs outputs.json --report report.md
```

The evaluator should:

- Match each output to a test case.
- Run deterministic checks.
- Compute summary metrics.
- Print failed cases.
- Produce a Markdown report.

### You Are Ready To Move On When

- You can build a repeatable evaluation script without manual spreadsheet work.
- You can explain every score in your report.
- You can rerun the same evaluation after a prompt or model change.

## Stage 3: LLM Output Evaluation

### Learn

- Instruction following evaluation.
- Helpfulness and completeness scoring.
- Factuality and hallucination checks.
- Refusal quality.
- Safety policy compliance.
- Prompt regression testing.
- Golden datasets vs flexible rubrics.
- LLM-as-judge strengths and weaknesses.

### Practice

- Build 50 test prompts for a support assistant, tutor, or research helper.
- Label each case by task type and risk level.
- Write expected facts and forbidden claims.
- Create a 1 to 5 rubric for answer quality.
- Compare two prompt versions using the same dataset.

### Mini Project

Create an LLM output evaluation suite with:

- Test dataset.
- Candidate outputs.
- Deterministic checks.
- Rubric scoring.
- Failure tags.
- Release decision.

Use `LLM_OUTPUT_EVALUATION_PYTHON_EXAMPLE.md` in this repo as a starting point.

### You Are Ready To Move On When

- You can separate "valid alternative wording" from "incorrect behavior."
- You can identify when exact match is too brittle.
- You can explain why a case failed in product terms, not only metric terms.

## Stage 4: RAG Evaluation

### Learn

- Retrieval recall.
- Context precision.
- Grounded answer quality.
- Citation correctness.
- Unsupported claim detection.
- Chunking and indexing effects.
- Query rewriting and reranking.
- Answer quality vs retrieval quality.

### Practice

- Build a small document corpus.
- Create questions with known supporting documents.
- Measure whether the correct document appears in top-k results.
- Check whether answers use only retrieved evidence.
- Tag failures as retrieval failure or generation failure.

### Mini Project

Build a RAG evaluation report with:

- Retrieval metrics: recall@k, precision@k, missing-document rate.
- Answer metrics: groundedness, completeness, citation accuracy.
- Failure examples.
- Recommendations for chunking, retrieval, prompt, or corpus fixes.

### You Are Ready To Move On When

- You can tell whether the retriever or generator caused a bad answer.
- You can evaluate citations instead of trusting that citations exist.
- You can explain how retrieval changes affect answer quality.

## Stage 5: Agent And Tool-Use Evaluation

### Learn

- Tool-call accuracy.
- Argument validation.
- Planning and step trace review.
- Permission and confirmation requirements.
- State management failures.
- Multi-step task success.
- Sandbox and side-effect safety.
- Cost and latency across multiple calls.

### Practice

- Define tasks that require tool use.
- Record agent traces.
- Check whether the correct tool was selected.
- Validate tool arguments.
- Score whether the final result matches the task.
- Identify unsafe or unnecessary actions.

### Mini Project

Evaluate a simple research or booking agent:

- Task set with expected outcomes.
- Tool-call trace logs.
- Tool correctness checks.
- Final answer quality rubric.
- Safety and permission checks.
- Cost and latency summary.

### You Are Ready To Move On When

- You can evaluate the process, not only the final answer.
- You can detect when an agent gets the right answer in an unsafe way.
- You can define safe tool-use boundaries.

## Stage 6: Human And Model Grading

### Learn

- Rubric design.
- Reviewer calibration.
- Inter-rater agreement.
- Blind review.
- Sampling strategies.
- LLM judge prompts.
- Judge bias and drift.
- Escalation from automated scoring to human review.

### Practice

- Write a rubric with score definitions from 1 to 5.
- Score the same 20 outputs twice and compare consistency.
- Ask another person or model to score the same outputs.
- Compare disagreements and refine the rubric.
- Add examples for each score level.

### Mini Project

Create a reviewer packet:

- Evaluation goal.
- Rubric.
- Examples of strong, weak, and unsafe answers.
- Review form.
- Calibration set.
- Disagreement resolution process.

### You Are Ready To Move On When

- Reviewers can apply your rubric consistently.
- You can explain when to trust a model judge and when to require human review.
- Your rubric catches severe failures even when the answer sounds fluent.

## Stage 7: Production Evaluation And Monitoring

### Learn

- Regression testing in CI.
- Canary releases.
- A/B testing basics.
- Production sampling.
- Drift monitoring.
- Incident review.
- Feedback loops.
- Cost, latency, and reliability dashboards.
- Data privacy and retention constraints.

### Practice

- Turn offline tests into regression tests.
- Define production metrics for quality, safety, latency, and cost.
- Create an incident template for AI failures.
- Sample live outputs for review.
- Compare production failures against offline test coverage.

### Mini Project

Design a production monitoring plan:

- What to log.
- What not to log.
- What metrics to track daily.
- What alerts should exist.
- What failures require human escalation.
- How new failures become regression tests.

### You Are Ready To Move On When

- You can connect offline evaluation to production monitoring.
- You can define alert thresholds for severe failures.
- You can turn real user failures into future test cases.

## Stage 8: Responsible AI And Risk

### Learn

- Privacy and data minimization.
- Bias and fairness testing.
- Safety policies and refusal behavior.
- High-risk domain evaluation.
- Red teaming.
- Abuse testing.
- Documentation and auditability.
- Human oversight.

### Practice

- Build adversarial prompts for one use case.
- Create subgroup or slice evaluations.
- Write refusal-quality examples.
- Define severity levels for failures.
- Document what data is used and why.

### Mini Project

Create a risk evaluation pack:

- Risk taxonomy.
- Safety test set.
- Privacy leakage checks.
- Fairness slices.
- Red-team examples.
- Mitigation recommendations.
- Signoff checklist.

### You Are Ready To Move On When

- You can evaluate harms, not just correctness.
- You can explain why some failures block release even if they are rare.
- You can document evaluation evidence for future review.

## Stage 9: Portfolio Projects

Build at least three portfolio projects.

### Project 1: LLM Output Evaluation

Evaluate a support, tutor, or writing assistant.

Include:

- Evaluation brief.
- Dataset.
- Rubric.
- Python evaluator.
- Report.
- Failure analysis.
- Before-and-after prompt comparison.

### Project 2: RAG Evaluation

Evaluate a knowledge assistant over a small document corpus.

Include:

- Document set.
- Question set.
- Ground-truth supporting documents.
- Retrieval metrics.
- Grounded answer scoring.
- Citation checks.
- Improvement plan.

### Project 3: Agent Evaluation

Evaluate a tool-using agent.

Include:

- Task set.
- Trace logs.
- Tool-call checks.
- Safety checks.
- Final answer scoring.
- Cost and latency summary.

### Optional Project 4: Production Monitoring Design

Create a monitoring plan for an AI feature.

Include:

- Metrics.
- Logs.
- Alerts.
- Sampling plan.
- Incident workflow.
- Regression feedback loop.

## Tooling To Learn

### Core

- Python
- `pandas`
- `pytest`
- JSON and CSV
- Git
- Markdown reports

### Evaluation And Experimentation

- Prompt/version tracking
- Dataset versioning
- Human review forms
- LLM judge prompts
- Regression suites
- Experiment logs

### Useful Libraries And Platforms

Specific tools change quickly, but the categories matter:

- LLM API clients
- Evaluation frameworks
- RAG frameworks
- Vector databases
- Observability platforms
- Annotation tools
- Dashboard tools
- CI systems

Do not become dependent on one tool. Learn the evaluation concepts deeply enough that
you can implement a small version yourself.

## 12-Week Study Plan

| Week | Focus | Deliverable |
| --- | --- | --- |
| 1 | Evaluation basics | Evaluation brief for one AI product |
| 2 | Metrics and risk | Risk map and release gate |
| 3 | Python evaluator basics | Script that scores outputs from JSON |
| 4 | Dataset design | 50-case LLM evaluation dataset |
| 5 | Rubric design | Human-readable quality rubric |
| 6 | LLM output evaluation | Full report comparing two prompt versions |
| 7 | RAG basics | Small corpus and question set |
| 8 | RAG evaluation | Retrieval and groundedness report |
| 9 | Agent evaluation | Tool-use task set and trace checks |
| 10 | Human/model grading | Calibrated review packet |
| 11 | Production monitoring | Monitoring and incident plan |
| 12 | Portfolio polish | Public case study with code and report |

## Common Mistakes To Avoid

- Evaluating only easy examples.
- Using one overall score without slice analysis.
- Treating fluent answers as correct answers.
- Trusting citations without checking support.
- Using an LLM judge without calibration.
- Moving release thresholds after seeing results.
- Ignoring severe failures because the average score is high.
- Testing only the model instead of the full system.
- Forgetting cost, latency, and operational reliability.
- Failing to turn production failures into regression tests.

## Interview Readiness

You should be able to answer:

- How would you evaluate a customer-support chatbot before launch?
- How would you design an evaluation dataset?
- How would you evaluate a RAG system separately from the LLM?
- How would you detect hallucinations?
- When would you use human review instead of automated scoring?
- What are the risks of LLM-as-judge evaluation?
- How would you define a release gate?
- How would you monitor an AI system after launch?
- How would you handle a high average score with a severe safety failure?

## Final Milestone

You are ready for AI evaluation engineering work when you can independently:

1. Understand the product decision.
2. Identify users, tasks, and risks.
3. Build a representative evaluation dataset.
4. Choose appropriate metrics and rubrics.
5. Implement a repeatable evaluation pipeline.
6. Interpret results without overclaiming.
7. Recommend concrete improvements.
8. Document evidence for a release decision.
9. Monitor behavior after deployment.

The best AI evaluation engineers are not just metric collectors. They are builders of
trustworthy evidence.
