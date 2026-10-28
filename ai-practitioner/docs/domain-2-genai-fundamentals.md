# Fundamentals of Generative AI

Exam weight: **24%**

## Big idea

A foundation model is a capable starting point, not a guarantee that an answer is factual, safe, or fit for a business process.

## Goal

Explain tokens, embeddings, transformers, inference, hallucinations, and the trade-offs among model capabilities and costs.

## Key words

- generative AI
- foundation models
- tokens
- embeddings
- transformers
- inference
- hallucinations
- temperature

## Notes

### From tokens to generated content

Text is processed as tokens. Transformer-based foundation models use learned relationships among tokens to generate a likely continuation. Embeddings represent semantic relationships in a numeric space and support similarity search.

### Capabilities have boundaries

A model can produce fluent but incorrect content, reflect training-data bias, or fail on a task outside its context. Latency, context length, quality, and token cost should be measured against the actual business use case.

## Capabilities in this domain

- [Foundation models](capabilities.md#foundation-models) — Start broad, then constrain and evaluate for a task.
- [Transformers](capabilities.md#transformers) — Model relationships among tokens with attention.
- [Tokens](capabilities.md#tokens) — Budget the units a model actually processes.
- [Embeddings](capabilities.md#embeddings) — Represent meaning as vectors.
- [Vector similarity](capabilities.md#vector-similarity) — Rank by geometry, then validate relevance.
- [Hallucination](capabilities.md#hallucination) — Detect unsupported claims and design abstention.

## Reflect

Describe one useful AI assistant capability and one control required before users rely on it.

## Mini checkpoint

### Q1. What is a token in a language-model workflow?

- A. A unit of text or other input processed by the model
- B. A permanent IAM credential
- C. A database backup
- D. A network Availability Zone

<details><summary>Answer</summary>

**A unit of text or other input processed by the model**

Models process input and output as tokens, which also commonly influence context and usage cost.

</details>

### Q2. What is a hallucination in a generative AI response?

- A. Plausible-sounding content that is unsupported or incorrect
- B. A model refusing every request
- C. A successful database failover
- D. An encrypted training example

<details><summary>Answer</summary>

**Plausible-sounding content that is unsupported or incorrect**

Generative models optimise likely output, so a fluent answer can still contain unsupported claims.

</details>

### Q3. What are embeddings commonly used for?

- A. Representing semantic relationships for similarity or retrieval
- B. Replacing all IAM policies
- C. Encrypting an AWS account root user
- D. Measuring CPU temperature

<details><summary>Answer</summary>

**Representing semantic relationships for similarity or retrieval**

Embeddings map content to vectors that can be compared for semantic similarity.

</details>
