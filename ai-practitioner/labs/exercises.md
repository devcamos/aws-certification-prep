# Hands-on exercises

For each exercise: build the smallest version, break it on purpose, then write what you learned.

## AI vs ML vs deep learning

**Goal:** Distinguish rules, conventional ML, deep learning, and generative AI from the required outcome.

### Build: Compare a rule with a learned score

Make encoded logic and learned parameters visibly different.

Suggested tools: simple code

Done when:
- Changing a weight changes a learned prediction.
- The README states what evidence would justify ML.

Example sketch:

```
record Ticket(double billing, double access) {}
static String rule(Ticket t) { return t.billing() > 0.5 ? "billing" : "access"; }
static String learned(Ticket t, double[] w) {
 return t.billing() * w[0] + t.access() * w[1] >= 0 ? "billing" : "access";
}
```

### Break it
Try:
- Swap the learned weights.
- Feed an example outside training coverage.

Watch for:
- Deterministic versus data-dependent failure
- Where abstention should begin

Recover by: Add an uncertainty threshold and route ambiguous cases to a human.

---

## Training vs inference

**Goal:** Trace data, parameters, versions, evaluation, deployment, and production predictions.

### Build: Freeze and version a tiny classifier

Prove inference is repeatable for an input and model version.

Suggested tools: simple code, JSON artifact

Done when:
- Repeated inputs produce the same score.
- Every output carries the model version.

Example sketch:

```
record Model(String version, double bias, double weight) {
 double infer(double x) { return 1.0 / (1.0 + Math.exp(-(bias + weight * x))); }
}
var model = new Model("router-7", -0.4, 1.7);
System.out.println(model.version() + ":" + model.infer(0.8));
```

### Break it
Try:
- Mutate weights between requests.
- Deploy without recording a version.

Watch for:
- Loss of reproducibility
- Missing rollback evidence

Recover by: Make artifacts immutable and promote versions only after evaluation.

---

## Foundation models

**Goal:** Explain pretraining, adaptation, model selection, and capability boundaries.

### Build: Call a local open model

Measure a model without an AWS dependency.

### Break it
Try:
- Stop the local model.
- Change model version without evaluation.

Watch for:
- Timeout behaviour
- Quality regression

Recover by: Bound requests with timeouts, pin versions, and block promotion on regression.

---

## Transformers

**Goal:** Explain self-attention, positional information, and context limitations.

### Build: Calculate attention weights

Make query-key weighting concrete.

Suggested tools: simple code

Done when:
- Weights sum to one.
- A larger score contributes more to the result.

Example sketch:

```
static double[] softmax(double[] s) {
 double max = Arrays.stream(s).max().orElseThrow();
 double[] e = Arrays.stream(s).map(v -> Math.exp(v - max)).toArray();
 double sum = Arrays.stream(e).sum();
 return Arrays.stream(e).map(v -> v / sum).toArray();
}
```

### Break it
Try:
- Remove position signals.
- Increase context sharply.

Watch for:
- Order ambiguity
- Memory and latency growth

Recover by: Use the smallest sufficient context and evaluate retrieval or summarisation.

---

## Tokens

**Goal:** Explain tokenisation, context, truncation, latency, and usage.

### Build: Add a conservative budget guard

Reject oversized requests before invocation.

Suggested tools: simple code, Real model tokeniser in production

Done when:
- The estimate is labelled non-authoritative.
- Output capacity is reserved.

Example sketch:

```
static int teachingEstimate(String text) {
 return (int) Math.ceil(text.codePointCount(0, text.length()) / 3.0);
}
static void requireBudget(String prompt, int max) {
 if (teachingEstimate(prompt) > max) throw new IllegalArgumentException("over budget");
}
```

### Break it
Try:
- Use emoji-heavy input.
- Set output reserve to zero.

Watch for:
- Estimate drift
- Truncated output

Recover by: Use the exact tokeniser and test representative languages and code.

---

## Embeddings

**Goal:** Explain generation, dimensions, semantic neighbourhoods, and model-version consistency.

### Build: Normalise teaching vectors

Treat vector dimensions and versions as explicit data.

Suggested tools: simple code

Done when:
- Normalised length is approximately one.
- Model version is stored with the index.

Example sketch:

```
static double[] normalise(double[] v) {
 double n = Math.sqrt(Arrays.stream(v).map(x -> x * x).sum());
 if (n == 0) throw new IllegalArgumentException("zero vector");
 return Arrays.stream(v).map(x -> x / n).toArray();
}
```

### Break it
Try:
- Mix dimensions.
- Re-embed half the corpus with a new model.

Watch for:
- Runtime rejection
- Meaningless cross-space scores

Recover by: Version preprocessing and rebuild indexes atomically.

---

## Vector similarity

**Goal:** Calculate cosine similarity and reason about top-k, thresholds, filters, and approximate search.

### Build: Rank with cosine similarity

Create an exact baseline before adding a vector database.

Suggested tools: simple code

Done when:
- Identical directions score near one.
- Invalid dimensions fail.

Example sketch:

```
static double cosine(double[] a, double[] b) {
 if (a.length != b.length) throw new IllegalArgumentException("dimension");
 double dot=0, aa=0, bb=0;
 for (int i=0;i<a.length;i++){ dot+=a[i]*b[i]; aa+=a[i]*a[i]; bb+=b[i]*b[i]; }
 if (aa==0 || bb==0) throw new IllegalArgumentException("zero");
 return dot/(Math.sqrt(aa)*Math.sqrt(bb));
}
```

### Break it
Try:
- Set top-k to the corpus size.
- Disable tenant filters.

Watch for:
- Context growth
- Cross-tenant leakage

Recover by: Separate access filtering from ranking and tune on labelled queries.

---

## Hallucination

**Goal:** Apply grounding, citation checks, evaluation, abstention, and human escalation.

### Build: Require supported citation IDs

Reject answers whose citations are absent from retrieved evidence.

Suggested tools: simple code

Done when:
- Unsupported citations trigger abstention.
- Plausible false answers are in tests.

Example sketch:

```
record Answer(String text, Set<String> citations) {}
static Answer requireGrounding(Answer a, Set<String> retrieved) {
 return a.citations().isEmpty() || !retrieved.containsAll(a.citations())
 ? new Answer("No approved evidence is available.", Set.of()) : a;
}
```

### Break it
Try:
- Use a real source ID for an unsupported claim.
- Retrieve the wrong document.

Watch for:
- Citation is not entailment
- Retrieval error propagation

Recover by: Evaluate retrieval and claim support separately; escalate high-impact uncertainty.

---

## Prompt engineering

**Goal:** Design trusted instructions, delimiters, examples, structured output, and injection boundaries.

### Build: Create a versioned Java prompt

Keep instructions, untrusted context, and output visibly separate.

Suggested tools: simple code, optional schema checks

Done when:
- Prompt version is recorded.
- Malformed output is rejected.

Example sketch:

```
record PromptInput(String question, String context) {}
static String build(PromptInput i) {
 return "SYSTEM: Answer only from CONTEXT. Return {answer,citations}.\n"
 + "CONTEXT_START\n" + i.context() + "\nCONTEXT_END\n"
 + "USER: " + i.question();
}
```

### Break it
Try:
- Insert an instruction into context.
- Remove the schema.

Watch for:
- Injection susceptibility
- Format failure

Recover by: Keep policy outside untrusted data, validate output, restrict tools, and add adversarial tests.

---

## Retrieval-augmented generation (RAG)

**Goal:** Trace ingestion, chunking, embedding, retrieval, prompting, citation, and evaluation.

### Build: Build in-memory Java retrieval

Filter, rank, and cite before adding a managed store.

Suggested tools: simple code, a local embedding helper

Done when:
- Only authorised chunks return.
- Every answer carries source IDs.

Example sketch:

```
record Chunk(String id, String tenant, String text, double[] vector) {}
static List<Chunk> retrieve(List<Chunk> chunks, String tenant, double[] q, int k) {
 return chunks.stream().filter(c -> c.tenant().equals(tenant))
 .sorted(Comparator.comparingDouble((Chunk c) -> cosine(q, c.vector())).reversed())
 .limit(k).toList();
}
```

### Break it
Try:
- Split a critical sentence.
- Remove tenant filter.
- Index stale versions.

Watch for:
- Lost context
- Data leakage
- Outdated answers

Recover by: Version sources, test chunking, authorize before retrieval, and support abstention.

---

## Fine-tuning

**Goal:** Choose adaptation only after prompts and retrieval are measured.

### Build: Validate a Java adaptation dataset

Make data quality and train/evaluation separation explicit.

Suggested tools: simple code, a local training run

Done when:
- No train/evaluation overlap.
- Base and adapted models run the same tests.

Example sketch:

```
record Example(String id, String input, String expected) {}
static void validate(List<Example> train, Set<String> evalIds) {
 var ids = new HashSet<String>();
 for (var e : train) if (!ids.add(e.id()) || evalIds.contains(e.id()))
 throw new IllegalArgumentException("duplicate or leakage");
}
```

### Break it
Try:
- Copy evaluation cases into training.
- Remove safety examples.

Watch for:
- Inflated score
- Safety regression

Recover by: Repair and version data, then promote only when all gates pass.

---

## Model evaluation

**Goal:** Design offline, human, operational, subgroup, and adversarial gates.

### Build: Compare candidate and baseline in Java

Fail promotion on explicit criteria.

Suggested tools: simple code, optional tests

Done when:
- Both versions use identical cases.
- Any required failure blocks promotion.

Example sketch:

```
record Score(double quality, long latencyMs, double cost) {}
static boolean passes(Score c, Score b) {
 return c.quality() >= 0.90 && c.quality() >= b.quality() - 0.01
 && c.latencyMs() <= 1500;
}
```

### Break it
Try:
- Test easy cases only.
- Average away one severe failure.

Watch for:
- Selection bias
- Hidden tail risk

Recover by: Version data and rubrics, report dimensions separately, and inspect severe failures.

---

## Responsible AI

**Goal:** Identify affected groups, test outcomes, document use, and retain accountable humans.

### Build: Measure subgroup false positives

Expose unequal error hidden by an aggregate.

Suggested tools: simple code

Done when:
- Aggregate and subgroup results are shown.
- Small samples are flagged.

Example sketch:

```
record Outcome(String group, boolean actual, boolean predicted) {}
static double fpr(List<Outcome> rows, String group) {
 var n = rows.stream().filter(r -> r.group().equals(group) && !r.actual()).toList();
 long fp = n.stream().filter(Outcome::predicted).count();
 return n.isEmpty() ? 0 : (double) fp / n.size();
}
```

### Break it
Try:
- Remove a group from tests.
- Automate without appeal.

Watch for:
- Coverage blind spot
- Missing accountability

Recover by: Repair representation, reassess thresholds, document limits, and preserve appeal.

---

## Guardrails

**Goal:** Place deterministic and model-assisted controls at correct layers.

### Build: Compose Java policy checks

Keep tool permission explicit.

Suggested tools: simple code

Done when:
- Disallowed tools fail closed.
- Tests cover bypass and overblocking.

Example sketch:

```
static final Set<String> ALLOWED = Set.of("searchCourseNotes");
static void authorise(String tool) {
 if (!ALLOWED.contains(tool)) throw new SecurityException("not allowed");
}
static String guard(String out) {
 return out.matches(".*\\b\\d{3}-\\d{2}-\\d{4}\\b.*") ? "withheld" : out;
}
```

### Break it
Try:
- Obfuscate sensitive text.
- Request a tool indirectly.

Watch for:
- Pattern bypass
- Intent versus string gap

Recover by: Layer permissions, classifiers, schema checks, adversarial tests, and escalation.

---

## AI security

> Study sketch only. No real passwords belong in this repo — use environment variables in your own sandbox if you try this.

**Goal:** Place IAM, encryption, TLS, mTLS, validation, minimisation, and audit correctly.

### Build: Create a Java mTLS client

Demonstrate mutual authentication at transport.

Suggested tools: an HTTP client, a keystore, a trust store

Done when:
- Server is validated.
- Unapproved clients fail.
- Authorization still checks actions.

Example sketch:

```
char[] password = System.getenv("MTLS_STORE_PASSWORD").toCharArray();
var keys = KeyStore.getInstance("PKCS12");
try (var in = Files.newInputStream(Path.of(System.getenv("MTLS_KEYSTORE")))) { keys.load(in, password); }
var kmf = KeyManagerFactory.getInstance(KeyManagerFactory.getDefaultAlgorithm());
kmf.init(keys, password);
var ssl = SSLContext.getInstance("TLS");
ssl.init(kmf.getKeyManagers(), null, new SecureRandom());
var client = HttpClient.newBuilder().sslContext(ssl).build();
```

### Break it
Try:
- Expire client certificate.
- Use untrusted CA.
- Log store password.

Watch for:
- Handshake failure
- Trust failure
- Secret exposure

Recover by: Automate rotation and revocation, fail closed, redact, and retain authorization.

---

## AI governance

**Goal:** Define inventory, owners, approvals, versions, evaluation, monitoring, incidents, and retirement.

### Build: Emit a Java AI decision record

Capture reproducibility without unnecessary sensitive content.

Suggested tools: simple code, an append-only log

Done when:
- Output links to model, prompt, sources, and evaluation.
- No secret or unnecessary learner data is stored.

Example sketch:

```
record AiDecisionRecord(UUID requestId, String useCaseId,
 String modelVersion, String promptVersion, List<String> sourceIds,
 String evaluationRelease, Instant occurredAt) {}
var record = new AiDecisionRecord(UUID.randomUUID(), "course-assistant",
 "model-7", "prompt-12", List.of("policy-2026-08"), "eval-44", Instant.now());
```

### Break it
Try:
- Remove prompt version.
- Allow unapproved model.
- Store every raw prompt forever.

Watch for:
- Lost reproducibility
- Policy bypass
- Privacy risk

Recover by: Validate evidence, enforce approved versions, and minimise audit data.

---