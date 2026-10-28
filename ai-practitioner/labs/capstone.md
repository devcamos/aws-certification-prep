# Capstone — grounded learning assistant

Design (and if useful, build a tiny version of) an assistant that answers from **my own AWS notes**.

## Must include

1. A foundation model accessed through Amazon Bedrock (or a local stand-in while learning)
2. Retrieval from a small set of approved notes (RAG)
3. Scoped access (least privilege) to model and data
4. Guardrails / output checks
5. A short evaluation set (quality, grounding, safety, cost/latency)
6. A responsible-AI review (who is affected, what can go wrong, human escalation)

## Questions to answer in writing

- When do I use RAG instead of fine-tuning?
- What must never go into a prompt?
- How do I prove an answer came from a note?
- What blocks a release if safety tests fail?

## Done looks like

A one- or two-page design note plus any small demo evidence (screenshots, logs, or a short README).