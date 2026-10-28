# Cloud Practitioner notes

Short summaries kept after passing CLF-C02.

## Cloud value, economics, and global infrastructure

**Principle:** Cloud architecture begins with business outcomes: agility, elasticity, resilience, reach, and variable cost.

**Goal:** Connect AWS global infrastructure and cloud economics to a personal project’s migration decision.

Key words: Regions, Availability Zones, edge locations, elasticity, agility, AWS CAF, Well-Architected

### Value before vocabulary

Cloud value is not simply renting somebody else’s server. Teams can provision capacity faster, scale with demand, reach more locations, and replace some capital planning with measured consumption. A good answer connects the benefit to the workload constraint.

### Regions, Availability Zones, and the edge

A Region is a geographic deployment boundary. Availability Zones are isolated locations within it that enable highly available regional designs. Edge locations bring content and network services nearer to users but do not replace a workload Region.

### Frameworks organise decisions

The AWS Cloud Adoption Framework helps organisations plan people, process, and technology change. The Well-Architected Framework reviews operational excellence, security, reliability, performance efficiency, cost optimisation, and sustainability.

### Checkpoint

### Q1. Which cloud benefit means adding and removing resources as demand changes?

- A. Elasticity
- B. Data sovereignty
- C. Capital expenditure
- D. Dedicated tenancy

<details><summary>Answer</summary>

**Elasticity**

Elasticity adjusts capacity to the workload rather than permanently provisioning for a possible peak.

</details>

### Q2. What is the primary architecture reason to use multiple Availability Zones in one Region?

- A. Regional high availability
- B. Lower every service price
- C. Replace IAM
- D. Create a global DNS namespace

<details><summary>Answer</summary>

**Regional high availability**

AZ separation reduces the chance that one facility-level failure removes the entire regional workload.

</details>

### Q3. What does the AWS Well-Architected Framework provide?

- A. A consistent way to review architecture trade-offs
- B. A fixed monthly AWS invoice
- C. A source-code licence
- D. A replacement for business requirements

<details><summary>Answer</summary>

**A consistent way to review architecture trade-offs**

The framework structures architecture reviews around six quality pillars.

</details>

Reflect: Explain why multiple Availability Zones and multiple Regions solve different business problems.

---

## Security, identity, and compliance

**Principle:** AWS secures the cloud; customers configure and protect what they run in the cloud.

**Goal:** Classify responsibilities and select identity, encryption, detection, and compliance services.

Key words: shared responsibility, IAM, MFA, least privilege, KMS, CloudTrail, Artifact, Shield

### Shared responsibility changes by service

AWS protects facilities, hardware, and managed-service foundations. Customers remain responsible for identities, data, configuration, and application code. Managed services move more operational work to AWS, but they do not remove customer accountability.

### Identity is the first control plane

Use the root user only for root-only tasks, protect it with MFA, prefer temporary role credentials, and grant only required actions on required resources. IAM policies express permissions; AWS Organizations and SCPs set broader account guardrails.

### Protection, detection, and evidence

KMS supports encryption-key control, CloudTrail records account API activity, CloudWatch observes workload behaviour, AWS Artifact provides compliance reports, and Shield/WAF address different network and application-layer threats.

### Checkpoint

### Q1. For Amazon RDS, who is responsible for protecting database credentials and application access?

- A. The customer
- B. AWS Support
- C. The hardware manufacturer
- D. The domain registrar

<details><summary>Answer</summary>

**The customer**

AWS manages the service infrastructure while the customer controls identities, credentials, data access, and application behaviour.

</details>

### Q2. Which service records AWS account API activity for audit and investigation?

- A. AWS CloudTrail
- B. Amazon CloudFront
- C. AWS Direct Connect
- D. Amazon Route 53

<details><summary>Answer</summary>

**AWS CloudTrail**

CloudTrail records control-plane activity and related identity context.

</details>

### Q3. What does least privilege require?

- A. Grant only the permissions needed for the task
- B. Give every engineer AdministratorAccess
- C. Use the root user for automation
- D. Disable logging to reduce cost

<details><summary>Answer</summary>

**Grant only the permissions needed for the task**

Least privilege limits the actions and resources available to an identity.

</details>

Reflect: Describe three security responsibilities a personal project retains when deployed to a managed AWS service.

---

## Core AWS technology and services

**Principle:** Certification questions reward the managed service that satisfies the requirement with the least unnecessary operational work.

**Goal:** Choose appropriate service families for common parts of a personal project.

Key words: EC2, Lambda, ECS, S3, EBS, EFS, RDS, DynamoDB, VPC, Route 53, CloudFront

### Compute choices express an operating model

EC2 provides virtual-machine control, Lambda runs event-driven functions, ECS orchestrates containers, and managed application platforms reduce infrastructure decisions further. Choose from the requirement, not from familiarity.

### Storage and databases are not interchangeable

S3 stores objects, EBS provides block storage for compute, and EFS provides shared file storage. RDS manages relational engines while DynamoDB provides a managed key-value and document database with different access-pattern trade-offs.

### Networks connect and deliver

A VPC is a regional network boundary, Route 53 provides DNS and routing policies, Elastic Load Balancing distributes traffic, and CloudFront caches content through a global edge network.

### Checkpoint

### Q1. Which AWS service is designed for durable object storage?

- A. Amazon S3
- B. Amazon EBS
- C. Amazon EC2
- D. AWS IAM

<details><summary>Answer</summary>

**Amazon S3**

S3 stores objects in buckets and supports lifecycle, replication, and multiple storage classes.

</details>

### Q2. Which managed service is the natural fit for an existing PostgreSQL application?

- A. Amazon RDS
- B. Amazon SQS
- C. Amazon CloudFront
- D. AWS Artifact

<details><summary>Answer</summary>

**Amazon RDS**

RDS supports managed PostgreSQL while retaining the relational database model.

</details>

### Q3. Which AWS service provides authoritative DNS and routing policies?

- A. Amazon Route 53
- B. AWS KMS
- C. Amazon ECR
- D. AWS CloudFormation

<details><summary>Answer</summary>

**Amazon Route 53**

Route 53 hosts DNS records and supports health-aware routing policies.

</details>

Reflect: Compare EC2, ECS Fargate, and Lambda as compute options for a personal project.

---

## Operations, billing, pricing, and support

**Principle:** Cloud cost is an architecture signal: measure it, allocate it, forecast it, and alert before it surprises you.

**Goal:** Select monitoring, cost-management, pricing, and support mechanisms for a small AWS workload.

Key words: CloudWatch, Health Dashboard, Cost Explorer, AWS Budgets, tags, On-Demand, Savings Plans, Spot, Support plans

### Monitoring and account health answer different questions

CloudWatch collects workload metrics, logs, and alarms. CloudTrail records API activity. AWS Health communicates events affecting AWS resources, while the public Service Health Dashboard communicates broader service status.

### Cost tools form a feedback loop

Cost Explorer analyses historical spend, AWS Budgets alerts against thresholds, the Pricing Calculator estimates proposed designs, and tags or cost categories allocate spend to owners and environments.

### Pricing models exchange flexibility for savings

On-Demand preserves flexibility, Savings Plans trade a usage commitment for lower eligible compute prices, and Spot uses spare capacity with interruption risk. Support plans differ in response times, guidance, and technical support access.

### Checkpoint

### Q1. Which service sends alerts when actual or forecast AWS spend crosses a threshold?

- A. AWS Budgets
- B. Amazon Route 53
- C. AWS Shield
- D. Amazon Inspector

<details><summary>Answer</summary>

**AWS Budgets**

Budgets evaluates configured cost or usage thresholds and sends notifications.

</details>

### Q2. Which service collects workload metrics and supports alarms?

- A. Amazon CloudWatch
- B. AWS Artifact
- C. AWS Organizations
- D. Amazon Cognito

<details><summary>Answer</summary>

**Amazon CloudWatch**

CloudWatch provides metrics, logs, dashboards, and alarms for AWS workloads.

</details>

### Q3. What is the defining trade-off of Spot capacity?

- A. Lower price with interruption risk
- B. Fixed capacity with no discount
- C. Global DNS with higher latency
- D. Permanent root credentials

<details><summary>Answer</summary>

**Lower price with interruption risk**

Spot uses spare AWS capacity and is appropriate only when the workload can tolerate interruption.

</details>

Reflect: Design a simple cost-control loop for a learner running temporary AWS labs.

---

## Practitioner capstone and exam readiness

**Principle:** Readiness means explaining the requirement-service relationship, not recognising a logo or memorising a question.

**Goal:** Produce a foundational cloud proposal for a personal project and complete the external readiness gate.

Key words: architecture brief, shared responsibility, service map, cost estimate, domain score, error log

### The capstone

Create a one-page proposal that identifies the users, Region, major AWS service families, security responsibilities, cost controls, and support path for a personal project. The proposal should be understandable without implementation detail.

### The external gate

Complete AWS Cloud Practitioner Essentials, the official question set, an official practice exam, and independent timed mocks. Record weak domains and revisit documentation until no domain remains below the readiness floor.

### Checkpoint

### Q1. What is the strongest reason to choose a managed AWS service?

- A. It
- B. It always has the lowest possible invoice
- C. It removes all customer security responsibilities
- D. It never experiences failure

<details><summary>Answer</summary>

**It**

Managed services can shift undifferentiated operations to AWS, but the architecture must still fit the requirements.

</details>

### Q2. Which result is the strongest readiness evidence?

- A. Consistent scores on fresh timed exams with explained mistakes
- B. Repeating one memorised mock until it reaches 100%
- C. Watching every video without practice
- D. Recognising most service icons

<details><summary>Answer</summary>

**Consistent scores on fresh timed exams with explained mistakes**

Fresh, timed, domain-balanced results test transfer and reveal unresolved reasoning gaps.

</details>

### Q3. What should a foundational architecture proposal lead with?

- A. Business and workload requirements
- B. The largest possible service list
- C. A root access key
- D. An assumption that every workload is serverless

<details><summary>Answer</summary>

**Business and workload requirements**

Requirements provide the basis for every service and architecture recommendation.

</details>

Reflect: Give a two-minute explanation of the proposed cloud architecture for a personal project to a non-technical stakeholder.

---