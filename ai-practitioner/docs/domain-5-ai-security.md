# Security, Compliance, and Governance for AI Solutions

Exam weight: **14%**

## Big idea

AI security extends familiar cloud controls with data lineage, prompt and output risks, model access, privacy, and continuous governance.

## Goal

Apply least privilege, encryption, secure data handling, monitoring, and governance to an Amazon Bedrock-based assistant.

## Key words

- Amazon Bedrock
- IAM
- KMS
- TLS
- mTLS
- CloudTrail
- Guardrails
- data privacy
- prompt injection
- governance
- auditability

## Notes

### Protect the data and the interfaces

Classify training and retrieval data, minimise sensitive content, encrypt data, restrict model and knowledge-base access, validate inputs, and treat prompts and model outputs as untrusted application data. Prompt injection and data leakage need application-layer controls as well as IAM.

### Govern the lifecycle

Record model and prompt versions, approval owners, evaluation results, and access events. AWS services such as IAM, KMS, CloudTrail, and Amazon Bedrock Guardrails can contribute controls, but the organisation remains responsible for its compliance obligations and intended use.

### Secure AI transport and workload identity

Use TLS for encrypted client-to-API and API-to-service transport. Where AI services communicate across a trusted service boundary and both workloads must prove identity, mTLS provides mutual certificate authentication; keep authorization, data filtering, and model guardrails at their respective application and policy layers.

## Capabilities in this domain

- [AI security](capabilities.md#ai-security) — Protect identity, data, transport, models, prompts, tools, and logs.
- [AI governance](capabilities.md#ai-governance) — Make ownership, policy, versions, evidence, and exceptions operational.

## Reflect

Describe how you would prevent learner records from being exposed through an AI assistant response.

## Mini checkpoint

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
