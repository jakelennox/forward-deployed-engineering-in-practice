# Glossary

Key terms defined by the course, copied verbatim from the course text saved locally in `docs/sources/` (gitignored). Later modules' questions and requests are checked against these meanings. When a module redefines a term, both definitions stay and the conflict is flagged for the engineer to resolve.

## Key terms (module 01)

| Term | Meaning | Source |
|---|---|---|
| Model (LLM) | Software that writes text by predicting likely next words. It knows nothing about Halyard unless it is given the text | module 01, Key Terms |
| Retrieval | Searching approved documents for passages related to the question before the model answers. Often called RAG, retrieval-augmented generation | module 01, Key Terms |
| Grounded answer | An answer in which every claim is supported by a retrieved passage | module 01, Key Terms |
| Citation | A pointer to the document and page or cell, so a person can check | module 01, Key Terms |
| Abstain | Say "I cannot answer from the sources you can access" instead of guessing | module 01, Key Terms |
| Hallucination | A confident answer that no source supports | module 01, Key Terms |
| Permission-aware | The search returns only documents the asking user may see | module 01, Key Terms |
| Eval | A repeatable set of test questions with expected behaviour, scored as pass rates | module 01, Key Terms |

## Terms defined in the module text (module 01)

| Term | Meaning | Source |
|---|---|---|
| Forward deployed engineer (FDE) | A software engineer who embeds with a customer, on-site, remotely or inside the customer's cloud/VPC (the customer's private cloud network), and owns a system end to end: scoping it, writing production code and keeping it running | module 01, Definition |
| VPC | The customer's private cloud network | module 01, Definition |
| Charter | One page that says what the engagement is for, what it excludes and who decides | module 01, Exercise 1 |
| Decision rights | Who may approve what | module 01, Exercise 1 |
| Evidence gate | What must be shown before release | module 01, Exercise 1 |
| SME | A subject-matter expert | module 01, Exercise 1 |
| Artefact | The document you would hand the client, such as docs/engagement-charter.md | module 01, Repository Map |
| Evidence file | A short note per exercise. It tells the reviewer what you did and links to the artefact. It does not repeat it | module 01, Repository Map |
| Responsible | Does the work | module 01, Exercise 2 table header |
| Accountable | Approves | module 01, Exercise 2 table header |

## Adjacent roles (module 01)

| Role | Typical centre of gravity | Example |
|---|---|---|
| Solutions Engineer | Configures an existing product | Demonstrates a vendor's connector and access model |
| Sales Engineer | Wins technical confidence before production hand-off | Runs a proof of concept for a buying decision |
| ML Engineer | Builds platform-side model and ML infrastructure | Maintains training and serving infrastructure |
| Product Engineer | Builds one-to-many product capabilities | Implements shared search features for many tenants |
| FDE | Embedded, end-to-end customer outcome | Discovers the workflow, ships permission-aware retrieval and arranges operations |

## Evidence labels

Kept in [evidence-labels.md](evidence-labels.md).
