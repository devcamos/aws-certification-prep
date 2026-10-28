# Fundamentals of AI and ML

Exam weight: **20%**

## Big idea

Start with the problem, data, and success measure before choosing an AI or ML technique.

## Goal

Distinguish AI, ML, deep learning, supervised learning, unsupervised learning, and common evaluation measures.

## Key words

- AI and ML
- training and inference
- supervised learning
- unsupervised learning
- classification
- regression
- overfitting

## Notes

### Match the technique to the task

Classification predicts a category, regression predicts a numeric value, clustering groups similar examples, and generative AI creates new content. The right choice depends on the desired output and the available labelled or unlabelled data.

### Measure what matters

Accuracy can hide an imbalanced-class problem. Precision, recall, F1 score, and a confusion matrix expose different error costs, while a validation set helps reveal overfitting before a model is used in production.

## Capabilities in this domain

- [AI vs ML vs deep learning](capabilities.md#ai-vs-ml-vs-deep-learning) — Choose the smallest capability that solves the problem.
- [Training vs inference](capabilities.md#training-vs-inference) — Separate learning parameters from using frozen parameters.

## Reflect

Explain which error matters more for a support router: a false escalation or a missed urgent request.

## Mini checkpoint

### Q1. Which ML task predicts a label such as billing, access, or technical?

- A. Classification
- B. Regression
- C. Clustering only
- D. Dimensionality reduction

<details><summary>Answer</summary>

**Classification**

Classification predicts one or more discrete categories.

</details>

### Q2. What is overfitting?

- A. A model memorises training patterns and performs poorly on new data
- B. A model has no training data
- C. A model always predicts the majority class correctly
- D. A model is encrypted at rest

<details><summary>Answer</summary>

**A model memorises training patterns and performs poorly on new data**

Overfitting occurs when a model learns training-specific noise rather than patterns that generalise.

</details>

### Q3. Which measures are useful when false positives and false negatives have different costs?

- A. Precision and recall
- B. Only training accuracy
- C. Storage capacity and latency
- D. Region count and instance size

<details><summary>Answer</summary>

**Precision and recall**

Precision and recall expose different classes of prediction error and are more informative than accuracy alone in many imbalanced problems.

</details>
