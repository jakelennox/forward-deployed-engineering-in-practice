# Ask Halyard role boundaries

- **Version:** 0.1 draft, 2026-11-24
- **Status:** Proposed by the FDE. **No approvals granted yet**; see the [approvals register](#approvals-register).
- **Companion:** [engagement-charter.md](engagement-charter.md)

## Purpose

Separate **who does the work** (Responsible) from **who is authorised to approve it** (Accountable) for the five activities where an embedded engineer is most tempted to act beyond their authority: discovery, source access, deployment, incident response and acceptance. Titles are fictitious; approvals are never invented.

## Roles

| Role | Fictitious title | Organisation | Notes |
|---|---|---|---|
| Sponsor | Head of Operations | Halyard | Owns budget, scope and release go/no-go. Name to confirm (charter A2). |
| FDE | Embedded forward deployed engineer (learner) | Delivery partner | Builds and runs the service; produces evidence. Cannot grant access or accept on Halyard's behalf. |
| Customer security | IT Security Manager | Halyard | Identity provider, entitlements, data classification, security incidents. Release veto on access grounds. |
| Operations lead | Operations Process Manager | Halyard | Owns the coordinator workflow, pilot users and business acceptance. Future service owner after handover. |
| Source owners | Policy/SOP owners per domain | Halyard | Decide which document version is authoritative. One per source (charter A1). |
| Legal/compliance | Legal Counsel / Data Protection Lead | Halyard | Confidentiality, personal data, contractual restrictions on content use. |
| Operations SME | Senior Operations Coordinator | Halyard | Writes and reviews the evaluation questions; judges answer correctness. |
| Customer IT platform | Infrastructure Lead | Halyard | Hosting, network, backups, change management for the runtime environment. |
| Sales lead | Head of Sales | Halyard | Consulted now; becomes an approver for sales sources in Release 2. |

## Responsibility matrix

R = Responsible (does the work), A = Accountable (approves; exactly one per activity), C = Consulted, I = Informed.

| Activity | FDE | Sponsor | Customer security | Operations lead | Source owners | Legal | Ops SME | Customer IT | Sales lead |
|---|---|---|---|---|---|---|---|---|---|
| **Discovery** (workflow interviews, problem framing, baseline, evaluation design) | **R** | **A** | C | C | C | I | C | I | C |
| **Source access** (granting read access to each document store and its entitlements) | R (requests, documents, implements read-only connector) | I | **A** | C | R (confirms authority and classification) | C | I | C | I |
| **Deployment** (each release into Halyard's environment) | **R** | C (go/no-go on scope) | C (access-control sign-off; veto) | C | I | I | I | **A** (change approval) | I |
| **Incident response** (outage, wrong answers, permission leak) | **R** (first responder during engagement; pauses path) | I | **A** for security incidents | **A** for service incidents | C | C (if confidential data exposed) | C | R (infrastructure) | I |
| **Acceptance** (business acceptance of each release) | R (presents evidence) | I | C (confirms access gates passed) | **A** | C | C | R (signs evaluation set and results) | I | I |

### Notes on the matrix

- **Incident response has two accountable roles by incident type, never both for the same incident.** Security incidents (any permission leak or data exposure) are accountable to customer security; service incidents (outage, degraded answers, stale sources) are accountable to the operations lead. Classification is made by customer security when in doubt.
- **Release go/no-go vs deployment approval.** The sponsor decides *whether* a scope is worth releasing; customer IT approves the *change* into their environment; customer security can block either on access grounds. The FDE can always *stop* a release on a failed gate but can never *approve* one.
- **Source access is split.** Source owners say a document is authoritative and how it is classified; customer security decides who may read it. The FDE implements both decisions and proves they hold on every retrieval path.

## Duties that remain with customer security and operations

These cannot be delegated to the FDE, even when the FDE has the technical ability to perform them.

**Customer security**
- Granting, changing and revoking access to source systems, service accounts and the identity provider.
- Defining data classification and the entitlement model that permission filtering mirrors.
- Declaring and leading security incidents, including deciding on notification.
- Signing off that permission tests cover every retrieval path (UI, HTTP API, MCP) before each release.
- Approving secrets management and audit-log retention.

**Operations**
- Deciding whether and how the coordinator workflow changes, and training pilot users.
- Naming authoritative source owners and resolving conflicting guidance.
- Business acceptance of each release against the evaluation evidence.
- Long-term service ownership after handover: on-call rota, backlog, decommission decision.
- Providing SME time for evaluation design and review.

**FDE (for contrast)**
- Discovery, design, implementation and evidence; first-line incident response during the engagement; pausing a path on a failed gate; preparing the handover pack so operations can take ownership.

## Approvals register

No approval below has been granted. Each row stays **Pending** until the approver confirms in writing, with date and reference.

| # | Approval | Approver | Needed before | Status |
|---|---|---|---|---|
| P1 | Charter scope, outcome and exclusions | Sponsor | Discovery begins | Pending |
| P2 | Sponsor identity and decision authority (charter A2) | Halyard leadership | P1 | Pending |
| P3 | Read access to operational SOP store (pilot domain) | Customer security | Feasibility | Pending |
| P4 | Authoritative owner per pilot source (charter A1) | Operations lead | Source ingestion | Pending |
| P5 | Local-first hosting and data residency (charter A7) | Customer security, customer IT | Proof of concept in Halyard's environment | Pending |
| P6 | SME time for 20-question set (charter A5) | Sponsor | Evaluation design | Pending |
| P7 | Reduced Release 1 scope after capacity halving | Sponsor | Replanning | Pending |
| P8 | Release 1 business acceptance | Operations lead | Pilot launch | Pending |

## Capacity reduction decision

**Scenario:** the sponsor reports that delivery capacity halves for the next quarter and the pilot date stays fixed.

**Principle:** keep the user outcome (faster access to approved, cited guidance) for a smaller group; shrink scope, not safety. Tell the sponsor exactly what was cut and get it approved (P7); never remove scope silently.

**What I stop doing first, in order:**

1. **Support-ticket summarisation model.** Highest novelty and evaluation cost, least tied to the Release 1 outcome. Defer entirely.
2. **MCP server.** An additional retrieval path that would need its own permission tests. Defer until a consumer exists.
3. **HTTP API for other tools.** Defer; the pilot uses a single interface, so one retrieval path to secure and test.
4. **Sales onboarding.** Sales sources (rate agreements, contract terms) carry the most complex entitlements. Defer to Release 2.
5. **Multiple document domains.** Pilot a single domain, operational SOPs and handling policies, chosen because most documents share one access group.
6. **Polish:** custom UI styling, analytics dashboards, conversational memory.

**What stays, unchanged:**

| Gate | Why it cannot be cut |
|---|---|
| Permission tests on every retrieval path that ships | A leak is irreversible and breaches legal's confidentiality requirement; fewer paths means fewer tests, not zero. |
| Restricted-document deny cases and cross-group checks | Even a mostly uniform domain contains restricted items. |
| SME-reviewed 20-question evaluation set | The only evidence that answers are correct; designed in discovery, run throughout. |
| Citation on every answer, abstention otherwise | Users must be able to verify guidance before acting. |
| Stop condition and escalation route | Defines what happens when something fails. |
| Named on-call owner before release | A running service with no owner is not a delivered service. |

**Effect:** roughly half the build surface is removed (one interface, one domain, one user group, no model training), while all six gates remain. The date can hold; if it cannot, the date moves, not the gates.

## Sources and interpretation

- **External research (course-supplied synthesis):** FDE Skills Report 2026 (117 postings, 78 companies), AI Engineer Insights "Forward-Deployed AI Engineer" (July 2026), InterviewBit "Forward Deployed Engineer Skills" (2026). Relevant points: compliance/GRC appears in 48% and OAuth/SSO in 43% of postings, and the synthesis calls evaluation engineering non-negotiable. These are posting mention frequencies, not time allocations, and they support directional priorities only. They justify treating access control and evaluation as first-class delivery work, which this matrix reflects.
- **Halyard assumptions (mine):** every title, role, headcount and approval route above is fictional and introduced for this exercise. None is a supplied fact.
