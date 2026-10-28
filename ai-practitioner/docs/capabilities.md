# Capability study cards

Each card is one skill. Learn the mechanism, then the AWS map, then practice.

## AI vs ML vs deep learning {#ai-vs-ml-vs-deep-learning}

**Domain:** Fundamentals of AI and ML

**Principle:** AI is the goal; ML learns patterns from data; deep learning is ML built from layered neural networks.

**Goal:** Distinguish rules, conventional ML, deep learning, and generative AI from the required outcome.

### Problem
A support router needs exact reasons for governed decisions but also sees wording that fixed rules miss.

### How it works
Rules encode decisions directly. ML estimates a mapping from examples. Deep networks learn multiple representation layers and usually require more data, compute, and controls.

### When to use / avoid
- Use: Use rules for explicit stable policy; use ML for repeatable patterns that rules cannot express economically.
- Avoid: Do not choose deep learning when deterministic code completely expresses the requirement.

Alternatives: Rules engine; Search; Human review; Conventional statistical model

### Trade-offs
- Learned systems generalise but are probabilistic.
- Expressive models cost more to train, evaluate, explain, and operate.

### Recall prompts
- Define AI, ML, and deep learning without naming a vendor.
- Give one task where a rule is stronger than ML.

### AWS map
- **Managed access to pretrained generative models** → Amazon Bedrock — Use when the task benefits from a foundation model without owning base-model infrastructure.
- **Build and host custom ML** → Amazon SageMaker AI — Use when the organisation owns the model lifecycle.

### Exam lens
Identify the output and constraints first; a service name does not turn a deterministic policy into ML.

### Quick questions
### Q1. Which relationship is correct?

- A. Deep learning is ML, and ML is one approach to AI
- B. AI is only deep learning
- C. ML is a database
- D. Deep learning is rule-only

<details><summary>Answer</summary>

**Deep learning is ML, and ML is one approach to AI**

The terms form a scope hierarchy.

</details>

### Q2. When is a rule usually preferable?

- A. Policy is deterministic and exactly explainable
- B. Input is high-dimensional audio
- C. Millions of labels exist
- D. Semantic generation is required

<details><summary>Answer</summary>

**Policy is deterministic and exactly explainable**

A complete explicit rule is simpler and more auditable.

</details>

---

## Training vs inference {#training-vs-inference}

**Domain:** Fundamentals of AI and ML

**Principle:** Training estimates parameters from evidence; inference applies an approved model version to new input.

**Goal:** Trace data, parameters, versions, evaluation, deployment, and production predictions.

### Problem
A classifier succeeds in a notebook but fails after release because test data, training, and live behaviour were mixed.

### How it works
Training updates parameters to reduce an objective. Validation estimates generalisation. Inference loads a fixed approved version and produces outputs without relearning from each request.

### When to use / avoid
- Use: Train only when an existing model cannot satisfy the measured task; serve immutable approved versions.
- Avoid: Do not train on test cases or silently update parameters inside production requests.

Alternatives: Pretrained model; Prompting; RAG; Rules

### Trade-offs
- Training adds data, compute, reproducibility, and governance cost.
- Batch inference trades freshness for cost; online inference adds latency and availability concerns.

### Recall prompts
- What changes during training?
- What stays stable during one governed inference request?

### AWS map
- **Managed training and hosted inference** → SageMaker training jobs and endpoints — They separate training from serving choices.
- **Managed foundation-model inference** → Amazon Bedrock — Applications invoke selected models without owning base-model training.

### Exam lens
Separate build-time learning from run-time prediction and choose inference mode from workload constraints.

### Quick questions
### Q1. What primarily changes during training?

- A. Model parameters
- B. TLS semantics
- C. DNS records per request
- D. IAM usernames

<details><summary>Answer</summary>

**Model parameters**

Training updates parameters from examples.

</details>

### Q2. Why record a model version with output?

- A. Reproduction, audit, and rollback
- B. Guaranteed correctness
- C. No drift
- D. Replacement for authorization

<details><summary>Answer</summary>

**Reproduction, audit, and rollback**

Version evidence identifies the artifact that served the request.

</details>

---

## Foundation models {#foundation-models}

**Domain:** Fundamentals of Generative AI

**Principle:** A foundation model is broadly pretrained for many downstream tasks; it is a component, not a complete product.

**Goal:** Explain pretraining, adaptation, model selection, and capability boundaries.

### Problem
A team needs summarisation and question answering but cannot train a large language model from scratch.

### How it works
Broad pretraining learns reusable representations. An application selects a model, supplies instructions and context, evaluates outputs, and adds controls around probabilistic generation.

### When to use / avoid
- Use: Use a foundation model for broad language or multimodal capability; select the smallest model meeting measured requirements.
- Avoid: Do not use one for exact policy code or assume it contains current private facts.

Alternatives: Rules; Task-specific ML; Search; Smaller local model

### Trade-offs
- Larger models may improve capability while raising cost and latency.
- Open models increase control and transfer hosting responsibility.

### Recall prompts
- What makes a model foundational?
- Why is it not a complete application?

### AWS map
- **Managed access to multiple foundation models** → Amazon Bedrock — Invoke supported models without managing base infrastructure.
- **Custom model lifecycle** → Amazon SageMaker AI — Own more training, hosting, and operations.

### Exam lens
Choose from modality, quality, latency, cost, context, and governance—not prestige.

### Quick questions
### Q1. What distinguishes a foundation model?

- A. Broad pretraining for many downstream tasks
- B. A fixed rule table
- C. Guaranteed factuality
- D. AWS dependency

<details><summary>Answer</summary>

**Broad pretraining for many downstream tasks**

Foundation models learn reusable capability before task adaptation.

</details>

### Q2. What is the strongest selection basis?

- A. Representative quality, latency, cost, and governance evidence
- B. Largest size
- C. Logo colour
- D. Assumed private knowledge

<details><summary>Answer</summary>

**Representative quality, latency, cost, and governance evidence**

Selection is a measured workload decision.

</details>

---

## Transformers {#transformers}

**Domain:** Fundamentals of Generative AI

**Principle:** Attention lets each token combine information from other relevant tokens.

**Goal:** Explain self-attention, positional information, and context limitations.

### Problem
A model must connect a pronoun to a noun many tokens earlier.

### How it works
Tokens produce query, key, and value representations. Query-key similarity yields weights over values; positional information preserves order. Repeated layers learn richer relationships.

### When to use / avoid
- Use: Use transformer models for sequence tasks needing contextual relationships.
- Avoid: Do not use them for simple exact parsing or equate attention with verified reasoning.

Alternatives: Parsers; Recurrent models; Search

### Trade-offs
- Standard attention grows expensive with sequence length.
- Long context raises compute without guaranteeing use of every fact.

### Recall prompts
- What do query, key, and value do?
- Why is positional information needed?

### AWS map
- **Invoke transformer-based models** → Amazon Bedrock — The service packages inference; attention remains a model mechanism.
- **Train or host custom transformers** → Amazon SageMaker AI — Use when owning the custom model lifecycle.

### Exam lens
Understand the mechanism and its limits independently of the managed service.

### Quick questions
### Q1. What does self-attention do?

- A. Weights relationships among token representations
- B. Encrypts traffic
- C. Creates IAM policy
- D. Stores vectors

<details><summary>Answer</summary>

**Weights relationships among token representations**

Attention combines information by learned relevance.

</details>

### Q2. Why is positional information needed?

- A. Attention alone does not encode order
- B. It grants permissions
- C. It guarantees citations
- D. It replaces tokens

<details><summary>Answer</summary>

**Attention alone does not encode order**

Position distinguishes reordered token sets.

</details>

---

## Tokens {#tokens}

**Domain:** Fundamentals of Generative AI

**Principle:** Models process token IDs, not human word counts; inputs and outputs share a finite context.

**Goal:** Explain tokenisation, context, truncation, latency, and usage.

### Problem
Instructions, history, sources, and requested output exceed the context even though each looks short.

### How it works
A model-specific tokeniser maps input to vocabulary IDs. Language, symbols, and code split differently, and all prompt regions plus generated output share the limit.

### When to use / avoid
- Use: Count with the selected model tokeniser and reserve output capacity.
- Avoid: Do not assume one token equals one word or truncate authoritative evidence silently.

Alternatives: Chunking; Retrieval; Summarisation; Shorter history

### Trade-offs
- More context costs latency and money.
- Truncation can remove decisive evidence; summaries can lose detail.

### Recall prompts
- Why is a token not always a word?
- What shares a context window?

### AWS map
- **Model-specific token limits and usage** → Amazon Bedrock model inference — Applications still own context and usage controls.
- **Select relevant context** → Knowledge Bases for Amazon Bedrock — Retrieval avoids appending every document.

### Exam lens
Relate tokens to context, latency, and cost using model-specific limits.

### Quick questions
### Q1. What is a token?

- A. A model-specific processed unit
- B. Exactly one word
- C. An access key
- D. A transaction

<details><summary>Answer</summary>

**A model-specific processed unit**

Tokenisers use model vocabularies, not universal word boundaries.

</details>

### Q2. Why reserve output capacity?

- A. Input and output share finite context
- B. TLS requires it
- C. Embeddings fail otherwise
- D. IAM blocks output

<details><summary>Answer</summary>

**Input and output share finite context**

An input-only budget can leave no room for generation.

</details>

---

## Embeddings {#embeddings}

**Domain:** Fundamentals of Generative AI

**Principle:** An embedding maps input to a vector whose learned geometry supports a similarity task.

**Goal:** Explain generation, dimensions, semantic neighbourhoods, and model-version consistency.

### Problem
Keyword search misses that 'mutual certificate authentication' relates to 'mTLS'.

### How it works
An embedding model maps items to fixed-length vectors and places related examples closer. Queries and documents must share a compatible model and preprocessing path.

### When to use / avoid
- Use: Use embeddings for semantic retrieval, clustering, recommendations, or deduplication.
- Avoid: Do not use them for exact identifiers or compare incompatible vector spaces.

Alternatives: Keyword search; Structured filters; Hybrid search

### Trade-offs
- Semantic recall can reduce exactness.
- Dimensions add storage and compute; embeddings can encode bias.

### Recall prompts
- What is an embedding?
- Why must vector spaces be compatible?

### AWS map
- **Generate semantic vectors** → Embedding models through Amazon Bedrock — The model produces vectors while the app owns compatibility.
- **Index vectors** → Amazon OpenSearch Service — Vector indexes support filtered nearest-neighbour retrieval.

### Exam lens
Distinguish embedding generation from storage and similarity search.

### Quick questions
### Q1. What is a common embedding purpose?

- A. Represent semantic relationships
- B. Encrypt parameters
- C. Replace all filters
- D. Create accounts

<details><summary>Answer</summary>

**Represent semantic relationships**

Embeddings provide numeric geometry for similarity.

</details>

### Q2. Why use compatible models for query and documents?

- A. Coordinates must share a learned space
- B. It removes bias
- C. It removes storage
- D. TLS requires it

<details><summary>Answer</summary>

**Coordinates must share a learned space**

Unrelated spaces do not preserve intended geometry.

</details>

---

## Vector similarity {#vector-similarity}

**Domain:** Fundamentals of Generative AI

**Principle:** Similarity is a ranking signal, not proof of equivalence, truth, or authorization.

**Goal:** Calculate cosine similarity and reason about top-k, thresholds, filters, and approximate search.

### Problem
A vector index must choose a small relevant set from thousands of notes.

### How it works
Cosine compares vector direction. An index retrieves high-scoring candidates, often approximately, before metadata filters or reranking.

### When to use / avoid
- Use: Use similarity to rank semantic candidates and tune on labelled queries.
- Avoid: Do not use it for authorization, exact IDs, or factual verification.

Alternatives: Exact lookup; Keyword ranking; Filters; Reranking

### Trade-offs
- Higher top-k improves recall and adds noise.
- Approximate indexes exchange exactness for speed.

### Recall prompts
- What does cosine compare?
- How do top-k and thresholds differ?

### AWS map
- **Vector search** → Amazon OpenSearch Service — Index vectors and filter candidates at scale.
- **Managed retrieval orchestration** → Knowledge Bases for Amazon Bedrock — Connect sources, embeddings, storage, and retrieval.

### Exam lens
Keep embeddings, stores, metrics, retrieval, and authorization distinct.

### Quick questions
### Q1. What does cosine similarity compare?

- A. Vector angle
- B. IAM length
- C. Certificate age
- D. Transaction count

<details><summary>Answer</summary>

**Vector angle**

Cosine compares direction while accounting for magnitude.

</details>

### Q2. Can similarity replace authorization?

- A. No, relevance and access are separate
- B. Yes above 0.9
- C. Yes for embeddings
- D. Yes at top-k one

<details><summary>Answer</summary>

**No, relevance and access are separate**

A score says nothing about caller permission.

</details>

---

## Hallucination {#hallucination}

**Domain:** Fundamentals of Generative AI

**Principle:** Fluent generation predicts plausible text; factual support requires evidence and verification outside the model.

**Goal:** Apply grounding, citation checks, evaluation, abstention, and human escalation.

### Problem
A course assistant invents a refund rule with confident wording.

### How it works
The model predicts likely tokens from context and parameters. Grounding supplies evidence; claim checks, citations, thresholds, and escalation constrain unsupported output.

### When to use / avoid
- Use: Ground claims that depend on current or private sources.
- Avoid: Do not let generated text execute authoritative transactions or equate low temperature with truth.

Alternatives: Exact lookup; Extractive answer; Search; Human response

### Trade-offs
- Abstention lowers harmful claims and answer coverage.
- Grounding inherits retrieval failures.

### Recall prompts
- Define hallucination.
- Name three impact controls.

### AWS map
- **Ground output in enterprise sources** → Knowledge Bases for Amazon Bedrock — Retrieved context can make answers traceable.
- **Evaluate and constrain behaviour** → Amazon Bedrock model evaluation and Guardrails — Measure behaviour and enforce configured policies.

### Exam lens
Select grounding, evaluation, and oversight from the consequence of an unsupported answer.

### Quick questions
### Q1. What is hallucination?

- A. Plausible unsupported or incorrect content
- B. A timeout
- C. An encrypted prompt
- D. A vector dimension

<details><summary>Answer</summary>

**Plausible unsupported or incorrect content**

Fluency can hide missing support.

</details>

### Q2. What should a high-impact assistant do without evidence?

- A. Abstain or escalate
- B. Invent
- C. Raise temperature
- D. Disable logs

<details><summary>Answer</summary>

**Abstain or escalate**

No-answer is safer than an unsupported authoritative claim.

</details>

---

## Prompt engineering {#prompt-engineering}

**Domain:** Applications of Foundation Models

**Principle:** A prompt is a contract for probabilistic behaviour; clarity helps, but evaluation proves it.

**Goal:** Design trusted instructions, delimiters, examples, structured output, and injection boundaries.

### Problem
A model returns inconsistent JSON and follows instructions embedded in untrusted notes.

### How it works
Prompts assemble trusted policy, user intent, untrusted context, examples, and an output contract. Validation and permissions handle non-compliance outside the model.

### When to use / avoid

### Trade-offs
- Long prompts raise clarity and token cost.
- Examples can anchor and bias behaviour.

### Recall prompts
- Name trusted and untrusted prompt regions.
- Why does an example not guarantee compliance?

### AWS map
- **Invoke with instructions and context** → Amazon Bedrock model inference — Applications supply versioned prompts.
- **Apply policy outside wording** → Guardrails for Amazon Bedrock — Configured controls complement prompts.

### Exam lens
Distinguish zero-shot, few-shot, structured output, and security boundaries.

### Quick questions
### Q1. What most improves reliable structured output?

- A. Explicit schema plus validation
- B. A vague request
- C. Secrets in prompt
- D. No constraints

<details><summary>Answer</summary>

**Explicit schema plus validation**

Prompting guides; validation protects consumers.

</details>

### Q2. Why is a system prompt not complete security?

- A. Deterministic tool, data, and output controls remain required
- B. Prompts are DNS
- C. TLS cannot carry prompts
- D. Models cannot read

<details><summary>Answer</summary>

**Deterministic tool, data, and output controls remain required**

Security is enforced outside probabilistic text.

</details>

---

## Retrieval-augmented generation (RAG) {#rag}

**Domain:** Applications of Foundation Models

**Principle:** RAG changes model context at inference; it neither retrains the model nor guarantees evidence.

**Goal:** Trace ingestion, chunking, embedding, retrieval, prompting, citation, and evaluation.

### Problem
An AWS tutor must answer from notes that change daily and cite an approved section.

### How it works
Documents are chunked, embedded, and indexed. Queries retrieve authorised candidates, optionally rerank them, and place evidence into the prompt before claim checks.

### When to use / avoid

### Trade-offs
- Small chunks improve precision and can lose context.
- Large top-k improves recall and adds noise, latency, and tokens.

### Recall prompts
- List the RAG pipeline.
- Where can it fail before generation?

### AWS map
- **Managed ingestion and retrieval** → Knowledge Bases for Amazon Bedrock — Orchestrate supported sources, embeddings, stores, and retrieval.
- **Source and vector storage** → Amazon S3 and Amazon OpenSearch Service — Source ownership and index design remain explicit.

### Exam lens
Choose RAG for current knowledge and fine-tuning for learned behaviour.

### Quick questions
### Q1. What is RAG's primary purpose?

- A. Provide external context at inference
- B. Update parameters per request
- C. Replace authorization
- D. Guarantee truth

<details><summary>Answer</summary>

**Provide external context at inference**

RAG retrieves evidence into context.

</details>

### Q2. Where should tenant authorization occur?

- A. Before or during retrieval
- B. Only in prose
- C. Through similarity
- D. Nowhere with citations

<details><summary>Answer</summary>

**Before or during retrieval**

Unauthorised chunks must not enter context.

</details>

---

## Fine-tuning {#fine-tuning}

**Domain:** Applications of Foundation Models

**Principle:** Fine-tuning changes parameters to make target behaviour likely; it is not a live knowledge database.

**Goal:** Choose adaptation only after prompts and retrieval are measured.

### Problem
A model knows the facts but uses the wrong labels and tone despite tested prompts.

### How it works
Input-output examples update all or some weights. The adapted artifact is versioned and compared with the base model for quality, safety, and retained capability.

### When to use / avoid

### Trade-offs
- Adaptation can improve consistency and reduce generality.
- Training adds governance and compute cost.

### Recall prompts
- What changes in fine-tuning?
- Why compare base and adapted models?

### AWS map
- **Adapt supported models** → Amazon Bedrock model customisation — Use supported methods for a measured behaviour goal.
- **Own custom training** → Amazon SageMaker AI — Control data, training, artifacts, and hosting.

### Exam lens
Fine-tuning changes behaviour; RAG supplies current context; prompting gives instructions.

### Quick questions
### Q1. What does fine-tuning change?

- A. Model parameters
- B. Source docs per request
- C. TLS certificates
- D. IAM groups

<details><summary>Answer</summary>

**Model parameters**

Fine-tuning optimises weights.

</details>

### Q2. Which need favours RAG?

- A. Changing knowledge requiring citations
- B. Stable tone
- C. Terminology
- D. Repeated format

<details><summary>Answer</summary>

**Changing knowledge requiring citations**

Retrieval supplies current evidence.

</details>

---

## Model evaluation {#model-evaluation}

**Domain:** Applications of Foundation Models

**Principle:** Evaluation tests a model-plus-application under representative conditions, not one benchmark.

**Goal:** Design offline, human, operational, subgroup, and adversarial gates.

### Problem
A model wins a public benchmark but gives worse grounded answers to learners.

### How it works
Versioned cases sample real tasks and failures. Automated metrics, rubrics, humans, latency, cost, and safety compare candidate and baseline before and after release.

### When to use / avoid

### Trade-offs
- Automated metrics scale and miss nuance.
- Human review adds nuance, cost, and variability.

### Recall prompts
- Why keep untouched evaluation cases?
- Name four dimensions beyond accuracy.

### AWS map
- **Evaluate foundation-model outputs** → Amazon Bedrock model evaluation — Compare supported models and criteria.
- **Analyse bias and drift** → SageMaker Clarify and Model Monitor — Support custom ML lifecycle evidence.

### Exam lens
Match methods and metrics to use case, error cost, and lifecycle stage.

### Quick questions
### Q1. What makes an evaluation set useful?

- A. Representative cases without training leakage
- B. Easy cases only
- C. Changing rubric
- D. Cost only

<details><summary>Answer</summary>

**Representative cases without training leakage**

Untouched cases estimate transfer.

</details>

### Q2. Quality rises but safety fails. What happens?

- A. Block promotion
- B. Average and ship
- C. Delete safety tests
- D. Hide baseline

<details><summary>Answer</summary>

**Block promotion**

A safety floor remains independent.

</details>

---

## Responsible AI {#responsible-ai-principles}

**Domain:** Guidelines for Responsible AI

**Principle:** Responsible AI is an organisational lifecycle practice, not a property a model owns.

**Goal:** Identify affected groups, test outcomes, document use, and retain accountable humans.

### Problem
An access model scores well overall but one group has twice the false-positive rate.

### How it works
Risk enters through samples, labels, features, objectives, thresholds, interfaces, and use. Teams define use, measure groups, document limits, provide review, and monitor.

### When to use / avoid

### Trade-offs
- Fairness definitions can conflict.
- Human review adds accountability and possible human bias.

### Recall prompts
- Where can bias enter?
- Why can fairness definitions conflict?

### AWS map
- **Measure bias and explain behaviour** → SageMaker Clarify — Support bias and explainability analysis.
- **Document and monitor use** → SageMaker Model Cards and Model Monitor — Retain lifecycle evidence.

### Exam lens
Keep fairness, explainability, privacy, safety, robustness, and oversight distinct.

### Quick questions
### Q1. Where can bias enter?

- A. Across data, objectives, deployment, and use
- B. Only UI colour
- C. Only inference
- D. Nowhere with accuracy

<details><summary>Answer</summary>

**Across data, objectives, deployment, and use**

Risk spans the lifecycle.

</details>

### Q2. Why retain human review?

- A. Challenge errors and preserve remedy
- B. Humans have no bias
- C. Avoid tests
- D. Make model deterministic

<details><summary>Answer</summary>

**Challenge errors and preserve remedy**

Oversight adds accountability.

</details>

---

## Guardrails {#guardrails}

**Domain:** Guidelines for Responsible AI

**Principle:** Guardrails reduce defined risks; they neither make models inherently safe nor replace authorization.

**Goal:** Place deterministic and model-assisted controls at correct layers.

### Problem
An assistant may leak records, follow injected text, or call a powerful tool.

### How it works
Input controls filter requests; data controls scope context; tool controls allow effects; output controls validate; monitoring and escalation handle misses.

### When to use / avoid

### Trade-offs
- Strict filters block harm and valid requests.
- Classifiers add nuance and latency.

### Recall prompts
- Name four guardrail layers.
- Define false positive and false negative.

### AWS map
- **Apply model-interaction policy** → Guardrails for Amazon Bedrock — Enforce configured content and sensitive-data controls.
- **Constrain effects and data** → IAM and application authorization — Permissions decide what workloads may do.

### Exam lens
Guardrails complement IAM, encryption, minimisation, evaluation, and oversight.

### Quick questions
### Q1. What is a guardrail's role?

- A. Reduce defined risks as one layer
- B. Guarantee safety
- C. Replace IAM
- D. Train models

<details><summary>Answer</summary>

**Reduce defined risks as one layer**

Guardrails retain scope and failure limits.

</details>

### Q2. What authorizes a financial action?

- A. Deterministic policy and permissions
- B. Model confidence
- C. Long prompt
- D. Similarity

<details><summary>Answer</summary>

**Deterministic policy and permissions**

Trusted code controls effects.

</details>

---

## AI security {#ai-security}

**Domain:** Security, Compliance, and Governance for AI Solutions

**Principle:** AI extends application security; model risks add layers without moving TLS or authorization.

**Goal:** Place IAM, encryption, TLS, mTLS, validation, minimisation, and audit correctly.

### Problem
A private AI workflow crosses networks, reads learner data, invokes a model, and calls tools.

### How it works
IAM authorizes. Encryption protects storage. TLS encrypts transport and authenticates servers; mTLS adds client-certificate authentication. Application controls scope data and effects.

### When to use / avoid

### Trade-offs
- mTLS adds rotation and revocation.
- Private networks do not encrypt or authorize alone.
- Logs can capture sensitive data.

### Recall prompts
- What does TLS provide?
- What does mTLS add and not add?

### AWS map
- **Manage certificates** → AWS Certificate Manager and AWS Private CA — Support public and private certificate lifecycle.
- **Mutually authenticate API transport** → Amazon API Gateway mTLS where appropriate — Authenticate client certificates at the API boundary.
- **Authorize model and data** → IAM, KMS, and scoped Bedrock permissions — Transport identity does not grant actions.

### Exam lens
TLS/mTLS is transport, IAM is authorization, KMS supports encryption, and guardrails govern model interaction.

### Quick questions
### Q1. What does mTLS add?

- A. Client certificate authentication in TLS
- B. Business authorization
- C. Factuality
- D. Vector encryption

<details><summary>Answer</summary>

**Client certificate authentication in TLS**

mTLS authenticates both transport peers.

</details>

### Q2. What controls which Bedrock model a workload invokes?

- A. Least-privilege IAM
- B. Similarity
- C. Certificate subject alone
- D. Prompt text

<details><summary>Answer</summary>

**Least-privilege IAM**

IAM authorizes AWS API actions.

</details>

---

## AI governance {#ai-governance}

**Domain:** Security, Compliance, and Governance for AI Solutions

**Principle:** Governance makes AI decisions attributable, reviewable, reproducible, and changeable.

**Goal:** Define inventory, owners, approvals, versions, evaluation, monitoring, incidents, and retirement.

### Problem
An auditor asks which model and prompt answered, who approved them, what data was allowed, and what evaluation passed.

### How it works
Governance links use case, owner, risk, lineage, model, prompt, evaluation, deployment, access, exception, incident, and retirement. Preventive controls block; detective controls reveal.

### When to use / avoid

### Trade-offs
- Controls can slow low-risk experiments without tiers.
- Audit data aids response and adds privacy duties.

### Recall prompts
- What makes output reproducible?
- Preventive versus detective control?

### AWS map
- **Record AWS API activity** → AWS CloudTrail — Investigate governed use and change.
- **Apply organisation permission guardrails** → AWS Organizations service control policies — Constrain actions without granting them.
- **Assess configuration and evidence** → AWS Config and AWS Audit Manager — Support detective controls and evidence.

### Exam lens
Separate governance, preventive control, detective evidence, compliance, and runtime security.

### Quick questions
### Q1. What best supports output reproducibility?

- A. Model, prompt, source, config, and evaluation versions
- B. Final prose only
- C. Developer only
- D. Invoice only

<details><summary>Answer</summary>

**Model, prompt, source, config, and evaluation versions**

Versioned artifacts connect output to context.

</details>

### Q2. What is a preventive control?

- A. Block unapproved deployment
- B. Review incident later
- C. Read logs
- D. Calculate cosine

<details><summary>Answer</summary>

**Block unapproved deployment**

Preventive controls stop non-compliant change.

</details>

---