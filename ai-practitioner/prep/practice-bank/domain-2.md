# Domain 2 — Fundamentals of Generative AI

38 practice questions.

### Q1. In generative AI, what is a token?

Format: single-choice · Task: 2.1 · Topic: tokens · Difficulty: easy

- **A.** A model-specific unit produced by a tokenizer that the model processes as input or output
- **B.** Exactly one English word in every language
- **C.** An AWS access key used to call foundation models
- **D.** A permanent database row that stores every past prompt

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Models consume and produce token IDs from a tokenizer vocabulary, not raw human word counts.
- **B:** Incorrect. Token boundaries vary by model and language; one word can map to several tokens or share a token.
- **C:** Incorrect. Access credentials authorize API calls; they are unrelated to how text is segmented for inference.
- **D:** Incorrect. Tokens are units of model computation within a request, not durable storage records.

</details>

### Q2. A prompt includes system instructions, chat history, retrieved documents, and space for the model reply. Why must the application reserve capacity for the reply?

Format: single-choice · Task: 2.1 · Topic: tokens · Difficulty: medium

- **A.** Input and generated output share one finite context window
- **B.** TLS encryption doubles the token count of every response
- **C.** Embeddings cannot be created unless the output reserve equals the input size
- **D.** IAM denies generation unless output tokens are prepaid as Provisioned Throughput

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Everything in the request plus tokens the model generates must fit within the model's context limit.
- **B:** Incorrect. Transport security does not change how many tokens the model allocates inside its context window.
- **C:** Incorrect. Embedding and generative context budgets are separate concerns; equal reserves are not required.
- **D:** Incorrect. IAM authorizes API actions; output reservation is a context-budget design choice, not a permission rule.

</details>

### Q3. What do text embeddings primarily represent?

Format: single-choice · Task: 2.1 · Topic: embeddings · Difficulty: easy

- **A.** Dense numeric vectors that place semantically related phrases near each other in vector space
- **B.** Human-readable labels that name every dimension of meaning
- **C.** Encrypted ciphertext of the original document
- **D.** Exact keyword indexes that only match identical strings

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Embedding models map text into vectors so similar meaning tends to produce similar geometry.
- **B:** Incorrect. Individual embedding dimensions rarely have simple natural-language labels.
- **C:** Incorrect. Embeddings are semantic representations, not cryptographic encryption of the source text.
- **D:** Incorrect. Keyword indexes support exact or lexical match; embeddings support semantic similarity.

</details>

### Q4. A retrieval pipeline embeds user queries with Model A and document chunks with Model B from a different family. What is the most likely problem?

Format: single-choice · Task: 2.1 · Topic: embeddings · Difficulty: medium

- **A.** Query and document vectors may not be comparable because embedding spaces are model-specific
- **B.** Amazon S3 will reject storing vectors from two models in the same bucket
- **C.** Tokenizers will automatically convert both models into one shared vocabulary
- **D.** Attention weights become negative and cancel retrieval scores

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Similarity search assumes a shared embedding space; mixing incompatible models breaks relevance ranking.
- **B:** Incorrect. Object storage does not enforce embedding-model compatibility; that is an application design concern.
- **C:** Incorrect. Tokenizers and embedding spaces stay tied to each model; they do not merge automatically.
- **D:** Incorrect. Attention is an internal transformer mechanism; this failure mode is about incompatible vector spaces.

</details>

### Q5. Which statements correctly describe self-attention in transformer models? (Select TWO.)

Format: multi-response · Task: 2.1 · Topic: transformers · Difficulty: medium

- **A.** Each token produces query, key, and value representations used to weight relationships among tokens
- **B.** Attention alone encodes absolute token order without any positional information
- **C.** Positional information helps the model distinguish sequences that share the same tokens in different order
- **D.** Self-attention guarantees that every attended token is factually verified against a knowledge base
- **E.** Attention scores are the same thing as AWS IAM permission boundaries

<details><summary>Answer</summary>

**Correct:** A, C

- **A:** Correct. Query-key similarity yields attention weights that combine value vectors from other tokens.
- **B:** Incorrect. Standard attention is permutation-sensitive only when positional signals are added separately.
- **C:** Correct. Position encodings or similar mechanisms supply order that bag-of-tokens attention would otherwise lose.
- **D:** Incorrect. Attention is a learned weighting mechanism, not a factuality or citation guarantee.
- **E:** Incorrect. Attention is an ML mechanism inside the model; IAM governs AWS API authorization.

</details>

### Q6. A team doubles the context window for every request so the model always sees the full document set. Which assessment is most accurate?

Format: single-choice · Task: 2.1 · Topic: transformers · Difficulty: hard

- **A.** Longer context raises compute and latency and still does not guarantee the model uses every fact
- **B.** Any increase in context length removes the need for retrieval or summarization forever
- **C.** Transformer attention becomes free once context exceeds one million tokens
- **D.** Positional encodings stop working when context is longer than the training prompt average

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Attention cost and latency grow with sequence length, and models can still underuse mid-context details.
- **B:** Incorrect. Retrieval and summarization remain useful when noise, cost, or relevance matter more than raw length.
- **C:** Incorrect. Longer sequences typically increase compute; there is no free threshold at one million tokens.
- **D:** Incorrect. Models may degrade on extreme lengths, but that is not the primary lesson versus cost and utilization.

</details>

### Q7. What best distinguishes a foundation model from a narrow task-specific model?

Format: single-choice · Task: 2.1 · Topic: foundation-models · Difficulty: easy

- **A.** It is broadly pretrained so it can be adapted to many downstream tasks
- **B.** It always returns deterministic, rule-checked answers
- **C.** It can only run on premises and never through a managed API
- **D.** It stores every enterprise fact permanently after one prompt

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Foundation models learn general representations during large-scale pretraining before task adaptation.
- **B:** Incorrect. Foundation models generate probabilistic outputs and still need application controls.
- **C:** Incorrect. Foundation models can be hosted privately or invoked through managed services such as Amazon Bedrock.
- **D:** Incorrect. A single prompt does not create durable enterprise knowledge inside the base model.

</details>

### Q8. When selecting a foundation model for a production workload, which basis is strongest?

Format: single-choice · Task: 2.1 · Topic: foundation-models · Difficulty: medium

- **A.** Measured quality, latency, cost, context limits, and governance fit on representative tasks
- **B.** Always pick the largest available parameter count
- **C.** Prefer whichever model has the most marketing screenshots
- **D.** Assume any foundation model already contains current private company facts

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Model choice is a workload decision backed by evidence, not brand prestige or size alone.
- **B:** Incorrect. Larger models can raise cost and latency without improving the measured business outcome.
- **C:** Incorrect. Marketing materials are not a substitute for evaluation on your data and constraints.
- **D:** Incorrect. Private and current facts must be supplied through authorized context or retrieval.

</details>

### Q9. What is a hallucination in generative AI?

Format: single-choice · Task: 2.2 · Topic: hallucinations · Difficulty: medium

- **A.** Fluent output that is unsupported by or contradicts the provided evidence or reality
- **B.** Any response that uses more than one paragraph
- **C.** A temporary AWS Region outage that blocks model invocation
- **D.** Correct retrieval of a cited source document

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. The model can produce confident text that is not grounded in facts or retrieved sources.
- **B:** Incorrect. Length alone does not define hallucination; unsupported claims do.
- **C:** Incorrect. Service availability issues are infrastructure problems, not generative hallucinations.
- **D:** Incorrect. Successful grounding with accurate citations is the opposite of hallucination.

</details>

### Q10. A customer-support assistant must reduce unsupported claims. Which practices help? (Select TWO.)

Format: multi-response · Task: 2.2 · Topic: hallucinations · Difficulty: hard

- **A.** Ground answers in retrieved enterprise sources and require citations when claims depend on those sources
- **B.** Allow the model to invent policy exceptions when retrieval returns no matches
- **C.** Add evaluation and policy controls such as Amazon Bedrock model evaluation and Guardrails where appropriate
- **D.** Disable logging so incorrect answers cannot be audited
- **E.** Assume doubling temperature always eliminates factual errors

<details><summary>Answer</summary>

**Correct:** A, C

- **A:** Correct. Retrieval grounding and citations make unsupported generation easier to detect and reject.
- **B:** Incorrect. Inventing policy is a high-risk hallucination pattern; abstention or escalation is safer.
- **C:** Correct. Measuring behaviour and enforcing configured policies complements prompt wording alone.
- **D:** Incorrect. Removing observability hides failures and blocks responsible improvement.
- **E:** Incorrect. Higher temperature usually increases randomness; it is not a factuality control.

</details>

### Q11. How do diffusion models typically generate images?

Format: single-choice · Task: 2.1 · Topic: diffusion-models · Difficulty: easy

- **A.** They iteratively denoise from a noisy starting point toward a sample matching the conditioning signal
- **B.** They look up the nearest exact stock photo by MD5 hash of the prompt
- **C.** They run only classical decision trees over pixel histograms
- **D.** They require the user to hand-paint every pixel before inference starts

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Diffusion generators reverse a noise process step by step, often guided by text or other conditions.
- **B:** Incorrect. Diffusion synthesizes new samples; it is not a deterministic file-hash lookup of existing assets.
- **C:** Incorrect. Decision trees are a different ML family and do not describe diffusion image generation.
- **D:** Incorrect. Users provide conditioning such as text; the model synthesizes the image.

</details>

### Q12. A product team wants text-to-image generation for marketing drafts and already uses Amazon Bedrock for language models. What is the most accurate GenAI concept statement?

Format: single-choice · Task: 2.1 · Topic: diffusion-models · Difficulty: medium

- **A.** Image generation often uses diffusion-style foundation models that are distinct from next-token language models
- **B.** Every language model can emit lossless PNG files by printing Base64 without a vision-capable generative path
- **C.** Diffusion models only classify images and never create new ones
- **D.** Image foundation models never accept text prompts as conditioning

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Text-to-image systems commonly rely on diffusion (or similar) generative processes rather than autoregressive token prediction alone.
- **B:** Incorrect. Reliable image generation needs an image-capable model or pipeline, not Base64 printing from a text-only LLM.
- **C:** Incorrect. Generative diffusion models are used to create new samples, not merely classify inputs.
- **D:** Incorrect. Text conditioning is a common control signal for modern text-to-image models.

</details>

### Q13. What does multimodal generative AI mean in practice?

Format: single-choice · Task: 2.1 · Topic: multimodal · Difficulty: medium

- **A.** The system can understand or generate across more than one modality, such as text, images, or audio
- **B.** The system must run in at least three AWS Regions at once
- **C.** The system can only answer multiple-choice exam questions
- **D.** The system refuses any prompt that mixes numbers and letters

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Multimodal models jointly handle multiple input or output types rather than text alone.
- **B:** Incorrect. Multimodality refers to data types, not multi-Region infrastructure.
- **C:** Incorrect. Exam formats are unrelated to multimodal model capabilities.
- **D:** Incorrect. Mixing characters in text is normal; multimodal refers to distinct media types.

</details>

### Q14. A retailer wants an assistant that answers questions about product photos and policy PDFs. Which statements are true? (Select TWO.)

Format: multi-response · Task: 2.2 · Topic: multimodal · Difficulty: medium

- **A.** A multimodal model can help when the question depends on visual content in the product photo
- **B.** Text-only embedding of filenames is always enough to describe what appears inside every photo
- **C.** Business limits still apply: visual answers can be wrong, biased, or expose sensitive image content without controls
- **D.** Multimodal models automatically grant IAM admin access to every object in Amazon S3
- **E.** PDFs never need chunking or retrieval once any multimodal model is selected

<details><summary>Answer</summary>

**Correct:** A, C

- **A:** Correct. Vision-language capability is useful when answers depend on image understanding.
- **B:** Incorrect. Filenames rarely capture visual detail; image understanding or image embeddings are needed.
- **C:** Correct. Multimodal GenAI inherits hallucination, privacy, and governance risks that must be managed.
- **D:** Incorrect. Model modality does not change AWS authorization; IAM still controls object access.
- **E:** Incorrect. Long documents still require context budgeting, chunking, or retrieval design.

</details>

### Q15. How are many foundation-model APIs, including Amazon Bedrock on-demand usage, commonly priced?

Format: single-choice · Task: 2.2 · Topic: token-pricing · Difficulty: easy

- **A.** By tokens processed for input and output, often at different rates per model
- **B.** By the number of IAM users in the AWS account only
- **C.** By the number of CSS pixels rendered in the front-end UI
- **D.** By a flat fee that never changes when prompt length grows

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Usage metering typically counts input and output tokens, and prices vary by model and modality.
- **B:** Incorrect. IAM user count is not the unit of generative inference billing.
- **C:** Incorrect. UI rendering is unrelated to model token metering.
- **D:** Incorrect. Longer prompts and completions usually increase billed token usage for on-demand calls.

</details>

### Q16. A chatbot appends the entire knowledge base to every user turn. What is the most direct cost and performance impact?

Format: single-choice · Task: 2.2 · Topic: token-pricing · Difficulty: medium

- **A.** Input token usage, latency, and spend rise because each request carries unnecessary context
- **B.** Output token prices fall to zero because the model caches the knowledge base forever
- **C.** Amazon CloudFront bills the tokens instead of the model provider
- **D.** Token pricing only applies when the response contains JSON

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Oversized prompts inflate billed input tokens and slow inference without guaranteeing better answers.
- **B:** Incorrect. Sending large context repeatedly still incurs input usage; there is no automatic free forever cache.
- **C:** Incorrect. CDN billing is separate; foundation-model usage is metered on the model invocation path.
- **D:** Incorrect. Token metering applies to model input and output regardless of response format.

</details>

### Q17. What is Amazon Bedrock primarily designed to provide?

Format: single-choice · Task: 2.3 · Topic: amazon-bedrock · Difficulty: easy

- **A.** Managed API access to foundation models from Amazon and third-party providers without managing base-model servers
- **B.** A replacement for IAM that removes the need for authentication
- **C.** A physical GPU shipment service for customer data centers only
- **D.** A spreadsheet tool that cannot call generative models

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Bedrock exposes supported foundation models through AWS APIs so teams skip owning base-model infrastructure.
- **B:** Incorrect. Bedrock invocations still use AWS identity and access controls.
- **C:** Incorrect. Bedrock is a managed cloud API service, not a hardware logistics product.
- **D:** Incorrect. Bedrock's purpose is foundation-model access and related generative AI capabilities.

</details>

### Q18. Which Amazon Bedrock capabilities help teams build governed GenAI applications? (Select TWO.)

Format: multi-response · Task: 2.3 · Topic: amazon-bedrock · Difficulty: medium

- **A.** Knowledge Bases for Amazon Bedrock to connect enterprise sources for retrieval-augmented generation
- **B.** Guardrails for Amazon Bedrock to apply configured content and sensitive-data policies around model interactions
- **C.** Automatic deletion of all CloudTrail logs that mention Bedrock API calls
- **D.** A setting that makes every model response legally binding without human review
- **E.** Replacing VPC networking with public anonymous access for all models

<details><summary>Answer</summary>

**Correct:** A, B

- **A:** Correct. Knowledge Bases help orchestrate ingestion, embeddings, storage, and retrieval for grounded answers.
- **B:** Correct. Guardrails add policy controls that complement prompts and application authorization.
- **C:** Incorrect. Governance needs auditability; deleting trails works against secure operations.
- **D:** Incorrect. No Bedrock switch converts probabilistic outputs into unchecked legal commitments.
- **E:** Incorrect. Secure designs retain identity, network, and data controls rather than anonymous public access.

</details>

### Q19. An architecture needs managed foundation-model inference today and may later customize supported models. Which AWS approach fits Domain 2 infrastructure choices?

Format: single-choice · Task: 2.3 · Topic: amazon-bedrock · Difficulty: hard

- **A.** Start with Amazon Bedrock for managed model access, and use Bedrock customization options or SageMaker AI when deeper training control is required
- **B.** Use Amazon Athena alone because SQL engines are foundation models
- **C.** Store prompts in Amazon SQS and assume no model endpoint is ever needed
- **D.** Disable all model choice and hard-code a single open-source binary into every Lambda layer forever

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Bedrock covers managed FM access and supported customization; SageMaker AI covers fuller custom ML lifecycle ownership.
- **B:** Incorrect. Athena is an interactive query service, not a foundation-model hosting platform.
- **C:** Incorrect. Queues move messages; generative inference still requires a model invocation path.
- **D:** Incorrect. Rigid packaging ignores Bedrock's multi-model flexibility and measured model selection.

</details>

### Q20. What is Amazon SageMaker JumpStart primarily used for?

Format: single-choice · Task: 2.3 · Topic: sagemaker-jumpstart · Difficulty: easy

- **A.** Discovering and deploying pretrained models and solutions quickly inside Amazon SageMaker AI
- **B.** Issuing temporary credit cards for third-party SaaS purchases
- **C.** Replacing Amazon VPC with a proprietary networking stack
- **D.** Compiling Java source code into JVM bytecode

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. JumpStart offers pretrained models and solution templates so teams can start faster on SageMaker AI.
- **B:** Incorrect. JumpStart is an ML model and solution hub, not a payments product.
- **C:** Incorrect. Networking remains an AWS infrastructure concern separate from JumpStart catalogs.
- **D:** Incorrect. Language compilation is unrelated to SageMaker JumpStart's pretrained model catalog.

</details>

### Q21. A team wants to fine-tune and host an open-weight language model with full control of training jobs and endpoints. Which pairing is most appropriate?

Format: single-choice · Task: 2.3 · Topic: sagemaker-jumpstart · Difficulty: medium

- **A.** Use Amazon SageMaker AI, optionally starting from a JumpStart model, when owning the custom training and hosting lifecycle
- **B.** Use Amazon Route 53 health checks as the model training cluster
- **C.** Use Amazon SNS topic filters to perform gradient updates
- **D.** Use AWS Budgets alerts as the inference endpoint

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. SageMaker AI is the broader custom ML platform; JumpStart accelerates starting from pretrained assets.
- **B:** Incorrect. DNS health checks do not train or host foundation models.
- **C:** Incorrect. Pub/sub filtering is not a training runtime for neural networks.
- **D:** Incorrect. Budget alerts monitor spend; they do not serve model predictions.

</details>

### Q22. Which statements correctly contrast Amazon Bedrock and Amazon SageMaker JumpStart for GenAI work? (Select TWO.)

Format: multi-response · Task: 2.3 · Topic: sagemaker-jumpstart · Difficulty: medium

- **A.** Bedrock emphasizes managed API access to foundation models without operating base-model servers
- **B.** SageMaker JumpStart helps teams find and deploy pretrained models within the SageMaker AI ML lifecycle
- **C.** JumpStart permanently replaces IAM for all AWS accounts that enable it
- **D.** Bedrock cannot be used for any generative language task by design
- **E.** Choosing JumpStart means prompts no longer consume tokens

<details><summary>Answer</summary>

**Correct:** A, B

- **A:** Correct. Bedrock's core value is managed FM inference and related application features.
- **B:** Correct. JumpStart sits in SageMaker AI where customers own more of training, hosting, and operations.
- **C:** Incorrect. Identity and access management remain required regardless of the ML service chosen.
- **D:** Incorrect. Language generation is a primary Bedrock use case.
- **E:** Incorrect. Hosted generative models still process tokens; the hosting platform does not remove that reality.

</details>

### Q23. What is Amazon Q in the AWS generative AI portfolio?

Format: single-choice · Task: 2.3 · Topic: amazon-q · Difficulty: easy

- **A.** A family of generative AI assistants, including Amazon Q Developer and Amazon Q Business, that help with software and enterprise work
- **B.** A relational database engine that replaces Amazon Aurora
- **C.** A hardware security module fleet sold only as appliances
- **D.** A deprecated name for Amazon Simple Queue Service

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Amazon Q products assist developers and business users with generative AI tailored to those workflows.
- **B:** Incorrect. Amazon Q is an assistant portfolio, not a relational database service.
- **C:** Incorrect. HSMs are a different AWS security category; Amazon Q is generative assistance software.
- **D:** Incorrect. Amazon SQS remains the queue service; Amazon Q is a separate GenAI assistant offering.

</details>

### Q24. A company wants employees to ask natural-language questions over internal wikis and ticketing systems with enterprise access controls. Which AWS GenAI product direction fits best?

Format: single-choice · Task: 2.3 · Topic: amazon-q · Difficulty: medium

- **A.** Amazon Q Business connected to authorized company data sources
- **B.** Amazon Macie alone with no generative assistant interface
- **C.** AWS Snowball Edge devices answering chat without any model
- **D.** Amazon CloudWatch alarms that rewrite wiki pages automatically

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Amazon Q Business is aimed at employee assistants over enterprise content with organizational controls.
- **B:** Incorrect. Macie helps discover sensitive data; it is not an employee Q&A assistant over wikis.
- **C:** Incorrect. Snowball is a data-transfer appliance family, not an enterprise chat assistant.
- **D:** Incorrect. CloudWatch monitors metrics and logs; it does not provide enterprise generative Q&A.

</details>

### Q25. In generative AI, what does an agentic application typically add beyond a single prompt-response call?

Format: single-choice · Task: 2.3 · Topic: agentic-ai · Difficulty: medium

- **A.** Planning or tool use so the system can take multi-step actions toward a goal under application controls
- **B.** Removing all authorization checks because the model is trusted
- **C.** Guaranteeing that every tool call is free of side effects
- **D.** Replacing metrics and logs with silent background execution

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Agents combine model reasoning with tools, memory, and orchestration rather than one-shot completion only.
- **B:** Incorrect. Agentic systems increase the need for scoped permissions, because tools can change real systems.
- **C:** Incorrect. Tools often have side effects; designs must constrain and audit them.
- **D:** Incorrect. Multi-step agents need stronger observability, not less.

</details>

### Q26. Which AWS building blocks are relevant when teams implement agentic GenAI applications? (Select TWO.)

Format: multi-response · Task: 2.3 · Topic: agentic-ai · Difficulty: hard

- **A.** Amazon Bedrock AgentCore for running and operating agents with managed runtime, memory, identity, and observability capabilities
- **B.** Strands Agents as an SDK approach for building and orchestrating model-driven agents that call tools
- **C.** Amazon Polly lexicons as the only required control plane for tool authorization
- **D.** AWS Glue crawlers that automatically approve production spend without human gates
- **E.** Amazon EMR bootstrap actions that disable CloudWatch for agent workloads

<details><summary>Answer</summary>

**Correct:** A, B

- **A:** Correct. Bedrock AgentCore provides infrastructure services that help deploy and operate agents at scale on AWS.
- **B:** Correct. Strands Agents is an AWS-oriented open SDK pattern for composing agent workflows and tool use.
- **C:** Incorrect. Polly is a text-to-speech service; tool authorization still depends on identity and application policy.
- **D:** Incorrect. Crawlers discover data catalogs; they do not replace agent spend or change-management controls.
- **E:** Incorrect. Turning off observability works against safe agent operations.

</details>

### Q27. Why do agentic GenAI systems need stronger identity and tool-permission design than a read-only chatbot?

Format: single-choice · Task: 2.3 · Topic: agentic-ai · Difficulty: medium

- **A.** Agents may invoke tools that change tickets, data, or infrastructure, so least-privilege scopes and audits matter more
- **B.** Agents never call external APIs, so permissions are decorative
- **C.** Foundation models automatically create temporary root users for each thought step
- **D.** Agent frameworks legally indemnify every incorrect tool call

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Tool-using agents expand the blast radius; authorization and observability become first-class controls.
- **B:** Incorrect. Tool calling is a defining agent capability and often reaches external systems.
- **C:** Incorrect. Models do not mint AWS root credentials as part of reasoning.
- **D:** Incorrect. Frameworks do not remove operational or compliance responsibility for actions taken.

</details>

### Q28. Which limitation should stakeholders expect from generative AI systems?

Format: single-choice · Task: 2.2 · Topic: genai-limitations · Difficulty: easy

- **A.** Outputs can be fluent yet incorrect, outdated, or missing private facts not supplied in context
- **B.** Models always refuse to answer until a human types the final sentence
- **C.** Generative models can never summarize text of any length
- **D.** Token limits disappear after the first successful API call

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Probabilistic generation does not guarantee truthfulness or access to unprovided private knowledge.
- **B:** Incorrect. Models can respond autonomously; human review is a design choice, not a universal limitation.
- **C:** Incorrect. Summarization is a common GenAI capability, though quality still needs evaluation.
- **D:** Incorrect. Context windows remain finite for subsequent calls.

</details>

### Q29. A finance process requires exact, repeatable calculation of tax rules from a codified policy engine. Why might GenAI be a poor primary solution?

Format: single-choice · Task: 2.2 · Topic: genai-limitations · Difficulty: medium

- **A.** Generative models are probabilistic and may invent steps instead of executing deterministic policy code
- **B.** Foundation models cannot be invoked from AWS accounts in any Region
- **C.** Tax rules are stored only as images that no OCR system can read
- **D.** Embeddings permanently delete source policy documents after vectorization

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Exact policy execution usually belongs in rules or deterministic services, with GenAI at most assisting explanation.
- **B:** Incorrect. AWS offers managed GenAI services; availability is not the core issue in this scenario.
- **C:** Incorrect. The scenario is about deterministic execution, not an assumed OCR impossibility.
- **D:** Incorrect. Embedding pipelines should retain source documents; deletion is not an inherent GenAI property.

</details>

### Q30. Which business risks are inherent enough that GenAI designs should plan mitigations up front? (Select TWO.)

Format: multi-response · Task: 2.2 · Topic: genai-limitations · Difficulty: hard

- **A.** Hallucinated or incomplete answers that users may trust because the tone sounds confident
- **B.** Cost and latency growth when prompts, history, and retrieved context expand without budgeting
- **C.** Guaranteed identical outputs for the same prompt across all model versions forever
- **D.** Automatic compliance with every global regulation without configuration
- **E.** Complete elimination of bias once a larger model is selected

<details><summary>Answer</summary>

**Correct:** A, B

- **A:** Correct. Fluency can mask error; grounding, evaluation, and human escalation are common mitigations.
- **B:** Correct. Token usage and long contexts directly affect spend and response time.
- **C:** Incorrect. Model updates and sampling mean behaviour can change; sameness is not guaranteed.
- **D:** Incorrect. Compliance remains an organizational responsibility with explicit controls.
- **E:** Incorrect. Larger models do not remove the need to assess and mitigate bias.

</details>

### Q31. What is the core idea of context engineering for GenAI applications?

Format: single-choice · Task: 2.2 · Topic: context-engineering · Difficulty: medium

- **A.** Deliberately selecting, structuring, and budgeting the information the model sees so it can perform the task reliably
- **B.** Encrypting the VPC CIDR range inside every user prompt
- **C.** Training a new foundation model from scratch for each user session
- **D.** Deleting evaluation datasets so prompts cannot be compared

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Context engineering treats instructions, history, tools, and retrieved evidence as a designed, limited resource.
- **B:** Incorrect. Network addressing does not belong in prompts and is not what context engineering means.
- **C:** Incorrect. Per-session pretraining is impractical; context engineering works with existing models.
- **D:** Incorrect. Evaluation remains essential; context engineering does not replace measurement.

</details>

### Q32. A support bot must answer from a large policy corpus without exceeding the model context window. Which design best reflects context engineering?

Format: single-choice · Task: 2.2 · Topic: context-engineering · Difficulty: hard

- **A.** Retrieve only the most relevant chunks, allocate budget across instructions, evidence, and output, and evaluate after trimming
- **B.** Paste the entire corpus into the system prompt on every request and ignore truncation errors
- **C.** Remove the user question so more policy text fits
- **D.** Replace retrieval with a random page from the corpus to reduce engineering effort

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Selective retrieval plus an explicit context budget preserves high-value evidence within limits.
- **B:** Incorrect. Blind pasting causes overflow, cost spikes, and uncontrolled truncation of important policy text.
- **C:** Incorrect. Without the question, the model lacks the task signal needed to answer correctly.
- **D:** Incorrect. Random context sacrifices relevance and increases wrong or incomplete answers.

</details>

### Q33. A localization team notices that the same user message costs more tokens in one language than another for the same model. What explains this best?

Format: single-choice · Task: 2.1 · Topic: tokens · Difficulty: hard

- **A.** Tokenizers are model- and vocabulary-specific, so languages and scripts can split into different token counts
- **B.** AWS bills an extra token for every Unicode code point in every Region
- **C.** Embeddings convert every language into exactly one token before generation
- **D.** Attention layers refuse multilingual prompts until they are translated to Morse code

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Non-English text, code, and symbols often tokenize less efficiently depending on the vocabulary.
- **B:** Incorrect. Billing follows the model's tokenizer usage, not a universal per-code-point AWS surcharge rule.
- **C:** Incorrect. Embeddings produce vectors; they do not collapse all languages to a single generative token.
- **D:** Incorrect. Multilingual prompts are routine; Morse code is unrelated to tokenization cost differences.

</details>

### Q34. A platform team is standardizing GenAI on AWS. Which statements about Amazon Bedrock are accurate? (Select TWO.)

Format: multi-response · Task: 2.3 · Topic: amazon-bedrock · Difficulty: medium

- **A.** Applications can invoke supported foundation models through AWS APIs while AWS manages the underlying model hosting for those offerings
- **B.** Teams can choose among multiple model providers and model IDs based on workload fit
- **C.** Bedrock removes the need for least-privilege IAM on InvokeModel and related actions
- **D.** Bedrock stores every prompt forever in a public bucket by default
- **E.** Using Bedrock means SageMaker AI can never be used in the same account

<details><summary>Answer</summary>

**Correct:** A, B

- **A:** Correct. Bedrock provides managed access so customers focus on application logic rather than base-model servers.
- **B:** Correct. Bedrock's catalog lets applications select models that match quality, latency, and modality needs.
- **C:** Incorrect. Bedrock API actions remain authorized through IAM policies.
- **D:** Incorrect. Customers control data handling; public default prompt dumps are not the service model.
- **E:** Incorrect. Accounts commonly combine Bedrock for managed FMs with SageMaker AI for custom ML work.

</details>

### Q35. An architect proposes storing 3,072-dimensional embeddings for every support ticket and comparing them with cosine similarity. Which trade-off should they communicate?

Format: single-choice · Task: 2.1 · Topic: embeddings · Difficulty: hard

- **A.** Higher dimensions can improve expressiveness while increasing storage, compute, and the need for compatible query embeddings
- **B.** Cosine similarity only works when vectors contain integers between 0 and 10
- **C.** Any embedding dimension above 32 makes retrieval mathematically impossible
- **D.** Similarity search replaces the need to secure source ticket content

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Embedding design trades semantic quality against cost, latency, and operational complexity.
- **B:** Incorrect. Cosine similarity works on real-valued vectors; integer-only ranges are not required.
- **C:** Incorrect. Production embedding models commonly use hundreds or thousands of dimensions.
- **D:** Incorrect. Authorization and privacy controls remain necessary for source data and derived vectors.

</details>

### Q36. A startup wants one foundation model to act as the entire product: billing, access control, audit, and customer UI. What is the best GenAI fundamentals critique?

Format: single-choice · Task: 2.2 · Topic: foundation-models · Difficulty: hard

- **A.** A foundation model is a component; applications still need product logic, security, evaluation, and operational controls around it
- **B.** Foundation models already include PCI-compliant billing ledgers for every industry
- **C.** Foundation models automatically issue unique IAM roles per generated sentence
- **D.** Foundation models remove the need to define user experience or error handling

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. FMs provide generative capability, not a complete governed business system by themselves.
- **B:** Incorrect. Payment and compliance systems are separate application responsibilities.
- **C:** Incorrect. Identity provisioning is an AWS and application concern, not a side effect of generation.
- **D:** Incorrect. UX, failures, and fallbacks remain product design work.

</details>

### Q37. Why do transformer language models need positional information in addition to token embeddings?

Format: single-choice · Task: 2.1 · Topic: transformers · Difficulty: easy

- **A.** Self-attention alone does not encode token order, so position signals distinguish different sequences
- **B.** Positional encodings are AWS Region codes embedded into every request
- **C.** Position vectors replace the need for a vocabulary or tokenizer
- **D.** Position information is only used when generating images with diffusion

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Without position, reordered tokens can look alike to attention over a bag of representations.
- **B:** Incorrect. Position refers to sequence order inside the model, not cloud Region identifiers.
- **C:** Incorrect. Models still tokenize text into vocabulary IDs; position supplements those embeddings.
- **D:** Incorrect. Positional signals are fundamental to transformer sequence modeling for language as well.

</details>

### Q38. Which practices are part of effective context engineering for a production GenAI assistant? (Select TWO.)

Format: multi-response · Task: 2.2 · Topic: context-engineering · Difficulty: medium

- **A.** Keep system instructions concise and versioned so behaviour changes are intentional
- **B.** Prefer relevant retrieved evidence over dumping entire corpora into the prompt
- **C.** Hide tool errors from logs so the model can invent successful outcomes
- **D.** Disable output reserves so completions can silently truncate mid-sentence forever
- **E.** Treat the context window as infinite once Provisioned Throughput is enabled
- **F.** Store API keys inside the system prompt so the model can rotate them

<details><summary>Answer</summary>

**Correct:** A, B

- **A:** Correct. Clear, versioned instructions make context changes reviewable and testable.
- **B:** Correct. Relevance-focused retrieval protects the context budget and improves answer quality.
- **C:** Incorrect. Suppressing tool failures encourages hallucination and blocks debugging.
- **D:** Incorrect. Reserving output capacity is part of responsible context budgeting.
- **E:** Incorrect. Provisioned Throughput affects capacity pricing and limits, not the model's finite context length.
- **F:** Incorrect. Secrets belong in secure secret stores and environment configuration, never in prompts.

</details>