# Applications of Foundation Models

Exam weight: **28%**

## Big idea

Reliable AI applications are systems around a model: context, instructions, tools, evaluation, guardrails, and observability all matter.

## Goal

Choose prompt engineering, retrieval-augmented generation, fine-tuning, and evaluation techniques for a grounded assistant.

## Key words

- prompt engineering
- zero-shot
- few-shot
- RAG
- fine-tuning
- Amazon Bedrock
- guardrails
- evaluation

## Notes

### Give the model the right context

Clear instructions, delimiters, examples, output schemas, and explicit constraints improve consistency. Retrieval-augmented generation supplies current domain context at request time, while fine-tuning adapts behaviour from curated examples rather than supplying a live knowledge source.

### Evaluate the whole application

Test factuality, relevance, safety, latency, cost, and refusal behaviour with representative examples. Amazon Bedrock provides managed access to foundation models and features such as model evaluation and guardrails that can support production workflows.

## Capabilities in this domain

- [Prompt engineering](capabilities.md#prompt-engineering) — Express task, context, constraints, and output contracts explicitly.
- [Retrieval-augmented generation (RAG)](capabilities.md#rag) — Retrieve current evidence before generation.
- [Fine-tuning](capabilities.md#fine-tuning) — Adapt behaviour with curated examples.
- [Model evaluation](capabilities.md#model-evaluation) — Turn quality, safety, latency, and cost into release evidence.

## Reflect

Explain why retrieval is preferable to retraining when the source documents change daily.

## Mini checkpoint

### Q1. What is the main purpose of retrieval-augmented generation?

- A. Provide relevant external context to the model at inference time
- B. Guarantee every generated answer is true
- C. Replace authentication
- D. Eliminate the need for evaluation

<details><summary>Answer</summary>

**Provide relevant external context to the model at inference time**

RAG retrieves information from a source and includes it in the generation context; it still requires quality and safety checks.

</details>

### Q2. Which prompt practice most improves structured API output?

- A. Specify the required schema, constraints, and an example
- B. Ask for anything without describing the output
- C. Remove all context
- D. Use a random temperature for every request

<details><summary>Answer</summary>

**Specify the required schema, constraints, and an example**

Explicit output requirements and examples make the desired response shape clearer to the model and the application.

</details>

### Q3. What is fine-tuning best described as?

- A. Adapting a pretrained model with curated examples for a target behaviour
- B. Adding live documents to a prompt at request time
- C. Increasing an IAM policy's permissions
- D. A replacement for monitoring

<details><summary>Answer</summary>

**Adapting a pretrained model with curated examples for a target behaviour**

Fine-tuning changes model behaviour from training examples; it is distinct from retrieving current knowledge at inference time.

</details>
