# Write the Engagement Charter

## Goal
Define embedded ownership for Ask Halyard in a bounded charter: a sponsor, a measurable user outcome, explicit exclusions, decision rights, an evidence gate and a stop condition, with supplied facts clearly separated from my assumptions.

## Steps taken
1. Created the course repository `forward-deployed-engineering-in-practice` with a [README](../../README.md), a [.gitignore](../../.gitignore) covering secrets, generated Halyard data, Node/TypeScript, Python, local models and editor files, and the [evidence template](../evidence-template.md) copied verbatim from module 01.
2. Drafted [docs/engagement-charter.md](../engagement-charter.md) from the course starter, replacing each example commitment with a reasoned decision and labelling every line as **[F]** supplied fact, **[A]** assumption or **[D]** decision proposal.
3. Translated the vague request ("an AI assistant for sales and ops") into a user outcome with a target (median time to an approved, cited answer under 2 minutes on the agreed question set) and stated that the baseline does not yet exist, rather than inventing one.
4. Sequenced users: operations coordinators pilot Release 1; sales follows once its sources and entitlements are mapped. HTTP API, MCP server and ticket summariser each get their own gate.
5. Listed exclusions beyond the starter (binding quotes, external customers, HR/personal data, training on customer data without legal approval).
6. Wrote seven open assumptions (A1 to A7), each with an owner, verification method and status.
7. Reviewed the charter against the three tensions (sponsor speed, legal confidentiality, operations reliability) and stated an order of precedence.
8. Answered "what would you stop doing first if delivery capacity halves" in a dedicated [charter section](../engagement-charter.md#if-delivery-capacity-halves): ordered stop-first list, the six gates that stay, and sponsor sign-off, linking to the full reasoning in [role-boundaries.md](../role-boundaries.md#capacity-reduction-decision).
9. Challenged the boundary: studying alone, I posed the sponsor's request to drop permission tests after capacity halves, and wrote a response that keeps the date and the permission gate by narrowing scope.

## Commands
~~~bash
mkdir -p ~/Dev/forward-deployed-engineering-in-practice/docs/01-the-forward-deployed-engineer-role
git -C ~/Dev/forward-deployed-engineering-in-practice init -b main
git -C ~/Dev/forward-deployed-engineering-in-practice switch -c 01-the-forward-deployed-engineer-role
git -C ~/Dev/forward-deployed-engineering-in-practice status --short
# count fact/assumption/decision labels and list sections
grep -c '\[A\]' docs/engagement-charter.md
grep -c '\[F\]' docs/engagement-charter.md
grep -c '\[D\]' docs/engagement-charter.md
grep -n '^## ' docs/engagement-charter.md
grep -c -i 'pending' docs/engagement-charter.md
~~~

## Results
Repository initialised and working on an exercise branch:

~~~text
Initialized empty Git repository in .../forward-deployed-engineering-in-practice/.git/
Switched to a new branch '01-the-forward-deployed-engineer-role'
?? .gitignore
?? README.md
?? docs/
~~~

Label counts in the charter (lines containing each label): `[A]` 6, `[F]` 11, `[D]` 12. Every charter-table row carries at least one label; detailed assumptions are in the separate A1 to A7 table.

Charter sections:

~~~text
7:## How to read this charter
15:## Supplied facts
24:## Charter
43:## Open assumptions
55:## Review against stakeholder tensions
65:## If delivery capacity halves
75:## Boundary challenge
98:## Change log
~~~

Summary of the charter's key commitments:

| Element | Commitment |
|---|---|
| Sponsor | Head of Operations (fictitious title, name to confirm) |
| Measurable outcome | Median time to approved, cited answer under 2 minutes; baseline measured in discovery |
| Exclusions | Shipment changes, legal/customs/contract advice, binding quotes, external customers, HR/personal data, training on customer data |
| Decision rights | Sponsor: scope and go/no-go; security: access, with release veto; ops lead: workflow and acceptance; source owners: authority; legal: confidentiality |
| Stop condition | Any permission leak pauses the affected path until security signs off the fix and regression test |
| Capacity halves | Stop first: ticket summariser → MCP server → HTTP API → sales onboarding → extra domains → polish; all six safety gates kept; sponsor sign-off (P7) pending |
| Approvals | None recorded as granted; explicit "pending" markers on sponsor approval, the reduced scope and the change log |

Boundary challenge (full text in the charter):

- **Question:** "We've lost half the team and the pilot date is fixed. Pilot users are internal, so drop the permission test suite for Release 1."
- **Response:** Decline removing the gate; internal staff have different entitlements. Keep the date by piloting one group on one document domain chosen for mostly uniform access, so the permission suite shrinks but still runs; defer API, MCP, ticket summariser and sales onboarding. Reduced scope recorded and sent for sponsor sign-off.

## Observations
- The hardest part was resisting a numeric baseline. A target like "under 2 minutes" is only meaningful against a measured starting point, so the baseline is an explicit assumption (A4) with an owner instead of a made-up figure.
- The starter's "Evidence gate: SME-reviewed questions and zero permission leaks" was missing citation coverage, abstention and an on-call owner. Without a named owner, a passing evaluation still leaves no one responsible when the service breaks, so I added it to the gate.
- Security holding a *veto* on access, rather than being one approver among several, is a deliberate choice: it stops a sponsor overriding an access concern to protect a date.
- "Internal users" is the most likely argument for weakening permission tests. Answering it in advance with concrete examples of cross-team sensitive content (contract margins, rate agreements, incident reports) made the response more persuasive than a principle alone.
- Follow-up: A1 (authoritative owners) and A3 (usable ACLs) are the riskiest assumptions and should lead the module 02 discovery and data inventory.
- Peer review: none available; the challenge was self-posed as the course allows.
