# Guidelines for Responsible AI

Exam weight: **14%**

## Big idea

Responsible AI is an ongoing product and governance practice, not a final checkbox after the model ships.

## Goal

Recognise bias, fairness, transparency, explainability, human oversight, and model monitoring responsibilities.

## Key words

- bias
- fairness
- transparency
- explainability
- human-in-the-loop
- robustness
- Amazon SageMaker Clarify
- Model Monitor

## Notes

### Risk enters through data and decisions

Training data can encode historical bias, missing groups, or proxy variables. Teams should document intended use, inspect data, test subgroup outcomes, and define escalation paths for high-impact decisions.

### Keep humans and evidence in the loop

Explainability helps stakeholders understand relevant factors; it does not prove a model is correct. Human review, feedback, drift monitoring, and repeatable evaluation keep accountability with the organisation using the system.

## Capabilities in this domain

- [Responsible AI](capabilities.md#responsible-ai-principles) — Design fairness, transparency, robustness, privacy, and accountability.
- [Guardrails](capabilities.md#guardrails) — Layer input, output, tool, and escalation policies.

## Reflect

Name two groups that could be affected by an automated learner-access decision and how you would test for disparate outcomes.

## Mini checkpoint

### Q1. Where can bias enter an ML system?

- A. Data, labels, features, modelling choices, and the way outputs are used
- B. Only the model's colour scheme
- C. Only after a database backup
- D. It cannot enter a trained system

<details><summary>Answer</summary>

**Data, labels, features, modelling choices, and the way outputs are used**

Bias can be introduced or amplified throughout the data, modelling, deployment, and decision lifecycle.

</details>

### Q2. Why use human oversight for a high-impact AI decision?

- A. A reviewer can challenge uncertain or harmful recommendations
- B. Humans make every model prediction mathematically identical
- C. It removes the need for testing
- D. It guarantees the model has no bias

<details><summary>Answer</summary>

**A reviewer can challenge uncertain or harmful recommendations**

Human review provides accountability and a path to challenge model output; it complements rather than replaces evaluation.

</details>

### Q3. What does explainability help a team do?

- A. Understand factors contributing to a model output and investigate errors
- B. Prove every prediction is correct
- C. Remove the need for access control
- D. Turn a classifier into a database

<details><summary>Answer</summary>

**Understand factors contributing to a model output and investigate errors**

Explainability supports review and debugging but is not a guarantee of correctness or fairness.

</details>
