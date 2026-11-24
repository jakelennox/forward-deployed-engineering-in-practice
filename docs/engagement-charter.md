# Ask Halyard engagement charter

- **Version:** 0.1 draft, 2026-11-24
- **Status:** Proposed by the FDE. **Sponsor approval pending.** Nothing in this charter is an approval until the named approver signs it off in the [approvals register](role-boundaries.md#approvals-register).
- **Companion:** [role-boundaries.md](role-boundaries.md) (responsibility matrix and capacity decision)

## How to read this charter

Every statement carries a label so a reviewer can see where it comes from:

- **[F] Fact:** supplied by the course brief. Not negotiable within this engagement.
- **[A] Assumption:** introduced by me to make the plan concrete. Must be confirmed or replaced during discovery; each has an owner in [Open assumptions](#open-assumptions).
- **[D] Decision proposal:** my reasoned recommendation as the embedded FDE. Becomes binding only when the role holding the decision right approves it.

## Supplied facts

- [F] Halyard Freight is a fictional mid-sized freight forwarder.
- [F] The product is **Ask Halyard**: a permission-aware knowledge assistant for sales and operations, with citations, an HTTP API, an MCP server and eventually a small model that summarises support tickets.
- [F] The FDE owns the engagement from discovery to handover: discovery → feasibility → proof of concept → production → evaluations and monitoring → handover and expansion. Evaluations are designed during discovery and run throughout.
- [F] This course delivers documents, not code. No GPU, cloud subscription or paid model API is available; the planned baseline is local-first (PostgreSQL 18 with pgvector, Ollama with `qwen3.5:4b`, `qwen3-embedding:0.6b`).
- [F] All data is fictional and the portfolio is public.
- [F] Autonomous shipment changes and legal advice are named as out of scope in the course starter.

## Charter

| Field | Commitment | Label |
|---|---|---|
| Sponsor | Halyard Head of Operations (fictitious title; **name to confirm**). Owns budget, scope and the release go/no-go. | [A] |
| Engineer | Learner acting as embedded FDE. Accountable for the delivered, running service and its evidence; not authorised to grant access or accept on Halyard's behalf. | [F]/[D] |
| Problem | Sales and operations staff lose time finding the *current, approved* version of operational guidance (SOPs, service policies, handling rules) and sometimes act on stale copies. | [A] |
| Outcome | Reduce the time a pilot user takes to find an approved, cited answer to an operational guidance question. **Target:** median under 2 minutes on the agreed question set, against a baseline measured in discovery (no baseline exists yet). | [D] target, [A] baseline |
| Quality floor | Every answer cites an approved source or explicitly abstains; correctness at least 85% on the SME-reviewed question set; **zero permission leaks**. | [D] |
| First users | Release 1 pilot: 10 to 15 operations coordinators at one site. Sales staff join in Release 2 once their source set and entitlements are mapped. Both groups are the intended users per the brief. | [F] users, [D] sequencing, [A] headcount |
| In scope (Release 1) | Read-only question answering over approved operational guidance documents, with citations, permission filtering at retrieval time, abstention when no approved source exists, and usage/feedback logging. | [D] |
| Later scope (own gates) | HTTP API for other internal tools; MCP server; support-ticket summarisation model. Each needs its own evidence gate and security review before release. | [F] capabilities, [D] gating |
| Not in scope | Autonomous or assisted shipment changes (no writes to booking/TMS systems); legal, customs-classification or contractual advice; binding price quotes; use by Halyard's external customers; HR or personal data sources; training or fine-tuning on customer data without separate legal approval. | [F] first two, [D] rest |
| Decision rights | Sponsor: scope, priorities, release go/no-go. Customer security: identity integration, source access, data classification; **holds a veto on release for access-control reasons**. Operations lead: workflow changes and business acceptance. Source owners: which document version is authoritative. Legal/compliance: confidentiality terms and any personal-data use. FDE: technical design, evidence, and the call to pause a release on failed gates. Detail in [role-boundaries.md](role-boundaries.md). | [D] |
| Evidence gate | Release 1 ships only when: (1) the 20-question evaluation set is reviewed and signed by an operations SME, including permission-denied and should-abstain cases; (2) zero permission leaks across all retrieval paths (UI, and API/MCP when they exist); (3) 100% of answered questions carry a resolvable citation; (4) correctness at or above the agreed floor; (5) a named on-call owner exists. | [D] |
| Stop condition | Any permission leak, in test or pilot, **pauses the release** of the affected path immediately; the FDE disables the path, notifies customer security the same business day and does not resume until security signs off the fix and the regression test. Also stop if a source has no authoritative owner (exclude the source) or the sponsor is unavailable for more than 10 working days (escalate). | [D] |
| Escalation | FDE → operations lead (workflow/acceptance issues) → sponsor (scope/priority conflicts). Security or confidentiality concerns go directly to customer security or legal and bypass the delivery chain. | [D] |
| Open assumption | Current policies have a named authoritative owner. Plus the list below. | [A] |

## Open assumptions

| # | Assumption | Why it matters | Owner to confirm | How to verify | Status |
|---|---|---|---|---|---|
| A1 | Every in-scope policy/SOP has a named authoritative owner. | Without an owner, "approved guidance" is undefined and citations cannot be trusted. | Operations lead | Source inventory in discovery (module 02 data inventory) | Open |
| A2 | Sponsor is the Head of Operations and holds budget and scope authority. | Decision rights in this charter depend on it. | FDE asks Halyard leadership | Written confirmation in approvals register | Open |
| A3 | Existing document stores expose per-document access groups that can be mirrored at retrieval time. | Permission-aware retrieval is impossible without a usable entitlement source. | Customer security | Access model walkthrough; sample of ACLs | Open |
| A4 | A time-to-answer baseline can be measured (task timing or helpdesk logs). | The outcome target is meaningless without a baseline. | FDE with operations lead | Timed tasks with 5 pilot users in discovery | Open |
| A5 | An operations SME has at least 4 hours to write and review the 20-question set. | The evidence gate depends on SME review. | Sponsor | Calendar commitment | Open |
| A6 | Pilot population is 10 to 15 coordinators at one site. | Sizes support load and evaluation coverage. | Operations lead | Named pilot list | Open |
| A7 | Local-first hosting inside Halyard's environment is acceptable to security. | Determines the deployment path and data residency. | Customer security | Security architecture review | Open |

## Review against stakeholder tensions

| Tension | What each party wants | How the charter resolves it |
|---|---|---|
| Sponsor wants speed | A visible win soon. | Start with one user group, one document domain and a read-only workflow. Speed comes from narrowing scope, never from skipping the evidence gate. |
| Legal wants confidentiality | No leakage of contract terms, customer data or privileged material. | Permission filtering at retrieval, not in the prompt; HR/personal data and customer-facing use excluded; local-first model so documents do not leave Halyard's environment (subject to A7); legal holds a decision right on any personal-data use. |
| Operations wants reliability | Answers they can act on, and a service that does not silently degrade. | Citations on every answer, abstention over guessing, SME-reviewed evaluation, a named on-call owner before release, and a stop condition that pauses rather than patches in production. |

Where the three conflict, the order of precedence is: **access control and confidentiality → correctness of guidance → delivery date**. A date can move; a leak cannot be undone.

## If delivery capacity halves

The user outcome stays (faster access to approved, cited guidance), delivered to a smaller group; scope shrinks, safety does not.

- **Stop first, in order:** support-ticket summarisation model → MCP server → HTTP API → sales onboarding → extra document domains → polish (UI styling, dashboards, conversational memory).
- **Keep, unchanged:** permission tests on every retrieval path that ships; restricted-document deny cases and cross-group checks; the SME-reviewed 20-question evaluation set; a citation on every answer or explicit abstention; the stop condition and escalation route; a named on-call owner before release.
- **Communicate:** the reduced scope goes to the sponsor for written sign-off (approval P7, pending); nothing is removed silently. If the reduced scope still cannot meet the date, the date moves, not the gates.

The reasoning behind each cut (outcome link, cost, risk and ordering) is in [role-boundaries.md](role-boundaries.md#capacity-reduction-decision).

## Boundary challenge

Studying alone, so the sponsor challenge is self-posed using the course's capacity scenario.

> **Sponsor (challenge):** "We've lost half the team for the next quarter and the pilot date is fixed. Pilot users are all internal Halyard staff anyway, so drop the permission test suite for Release 1 and add it before the wider rollout."

**Written response (FDE):**

I can't remove the permission gate, but I can keep your date by shrinking what we ship.

"Internal" does not mean "same entitlements". Operations coordinators should not see sales contract margins, customer-specific rate agreements or security incident reports, and that is exactly the content a retrieval system will surface if access is not enforced on every query. A leak in a pilot is still a leak: it would breach legal's confidentiality requirement and the charter's stop condition, and it would cost more time than the tests save.

What I propose instead:

1. Pilot one user group (operations coordinators) on one document domain (operational SOPs and handling policies).
2. Choose that domain so most documents share a single access group. The permission test suite stays, but becomes smaller: deny cases for the handful of restricted documents plus a cross-group check, rather than a full entitlement matrix.
3. Defer the HTTP API, MCP server, ticket summariser and sales onboarding to later releases, each with its own gate.
4. Keep the SME-reviewed 20-question set, citations and the stop condition unchanged.

Outcome for you: the date holds, the user outcome (faster access to approved guidance) holds for the pilot group, and nothing about the reduced scope is hidden; it is recorded in [role-boundaries.md](role-boundaries.md#capacity-reduction-decision) and needs your sign-off.

**Status:** response drafted; sponsor sign-off on the reduced scope **pending**.

## Change log

| Date | Version | Change | Approved by |
|---|---|---|---|
| 2026-11-24 | 0.1 | Initial draft | Pending |
