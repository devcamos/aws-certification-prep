# Practice questions (checkpoints)

These come from the domain and capability checkpoints in my study material.
Answers are hidden behind expandable sections.

For a larger bank, see [practice-bank/](practice-bank/).

## Domain exam checkpoints

### AI and ML fundamentals domain exam

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

### Generative AI fundamentals domain exam

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

### Applications of foundation models domain exam

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

### Responsible AI domain exam

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

### Security, compliance and governance domain exam

### Q1. Which IAM approach is most appropriate for an AI application?

- A. A scoped workload role with only the required model and data permissions
- B. A root access key embedded in the prompt
- C. AdministratorAccess for every user
- D. A public bucket containing all learner data

<details><summary>Answer</summary>

**A scoped workload role with only the required model and data permissions**

Least privilege limits the blast radius of application compromise and accidental misuse.

</details>

### Q2. What is a sound first step before using learner records in an AI workflow?

- A. Classify and minimise the data, then confirm the approved purpose and controls
- B. Copy every record into a public prompt
- C. Disable audit logging
- D. Assume a model makes private data safe automatically

<details><summary>Answer</summary>

**Classify and minimise the data, then confirm the approved purpose and controls**

Data minimisation and purpose-driven governance reduce privacy exposure before a model is involved.

</details>

### Q3. Why retain model, prompt, access, and evaluation records?

- A. To support accountability, investigation, reproducibility, and compliance review
- B. To guarantee outputs never change
- C. To replace encryption
- D. To make the model larger

<details><summary>Answer</summary>

**To support accountability, investigation, reproducibility, and compliance review**

Lifecycle evidence helps teams understand what was deployed, who used it, how it performed, and why decisions were made.

</details>
## Capability checkpoints

### AI vs ML vs deep learning

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

### Training vs inference

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

### Foundation models

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

### Transformers

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

### Tokens

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

### Embeddings

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

### Vector similarity

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

### Hallucination

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

### Prompt engineering

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

### Retrieval-augmented generation (RAG)

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

### Fine-tuning

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

### Model evaluation

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

### Responsible AI

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

### Guardrails

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

### AI security

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

### AI governance

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