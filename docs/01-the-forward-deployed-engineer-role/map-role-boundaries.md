# Map Role Boundaries

## Goal
Turn the course's role comparisons into delivery accountability for Ask Halyard: a reviewable responsibility matrix for discovery, source access, deployment, incidents and acceptance, the duties that stay with customer security and operations, and a capacity-reduction decision that keeps every safety gate.

## Steps taken
1. Defined nine roles in [docs/role-boundaries.md](../role-boundaries.md#roles) with fictitious titles, separating Halyard roles from the delivery-partner FDE.
2. Built the [responsibility matrix](../role-boundaries.md#responsibility-matrix) for the five activities, separating Responsible (does the work) from Accountable (authorised to approve), with one accountable role per activity. The exception is incident response, where accountability splits by incident *type* (security vs service) and is never shared for one incident.
3. Listed the [duties that remain with customer security and operations](../role-boundaries.md#duties-that-remain-with-customer-security-and-operations) even when the FDE has the technical ability to perform them.
4. Created an [approvals register](../role-boundaries.md#approvals-register) of eight approvals (P1 to P8), all marked **Pending**, linked to charter assumptions A1, A2, A5 and A7. No approval was invented.
5. Wrote the [capacity reduction decision](../role-boundaries.md#capacity-reduction-decision): an ordered list of what to stop first, the six gates that stay, and the rule that the date moves before the gates do.
6. Separated external research from my Halyard assumptions in [Sources and interpretation](../role-boundaries.md#sources-and-interpretation).
7. Tagged the module's final commit `module-01`.

## Commands
~~~bash
grep -n '^## ' docs/role-boundaries.md
# every approval row must still read Pending
grep -c '| Pending |' docs/role-boundaries.md
# look for any wording that claims an approval was given
grep -ni 'approved\b\|granted on' docs/role-boundaries.md
# count bold accountable cells in the matrix
grep -o '\*\*A\*\*' docs/role-boundaries.md | wc -l
git status --short
git tag module-01
~~~

## Results
Sections in the artefact:

~~~text
7:## Purpose
11:## Roles
25:## Responsibility matrix
43:## Duties that remain with customer security and operations
64:## Approvals register
79:## Capacity reduction decision
107:## Sources and interpretation
~~~

Approval checks:

~~~text
8      # rows marked "| Pending |" (P1 to P8, all of them)
83:**Principle:** ... Tell the sponsor exactly what was cut and get it approved (P7); never remove scope silently.
~~~

The only match for approval wording is an instruction to *seek* approval, not a claim that one exists.

Accountable cells: 6 bold **A** entries across 5 activities (discovery, source access, deployment, acceptance each have one; incident response has two, split by incident type).

Matrix summary (who approves vs who does):

| Activity | Accountable | Responsible |
|---|---|---|
| Discovery | Sponsor | FDE |
| Source access | Customer security | FDE (request, connector) and source owners (authority, classification) |
| Deployment | Customer IT (change approval); security can veto | FDE |
| Incident response | Security (security incidents) / operations lead (service incidents) | FDE first response; customer IT for infrastructure |
| Acceptance | Operations lead | FDE (evidence) and ops SME (evaluation sign-off) |

Capacity decision, stop first in order: ticket summariser → MCP server → HTTP API → sales onboarding → extra document domains → polish. Retained: permission tests on every shipped path; restricted-document deny cases; SME-reviewed 20-question set; citations or abstention; stop condition and escalation; named on-call owner.

## Observations
- Applying "exactly one accountable role" to incident response did not work: the security manager should not own an outage, and the operations lead should not own a data exposure. Splitting by incident type, with security deciding classification when unclear, kept one accountable role per *incident*.
- Deployment has three distinct decisions that are easy to merge: sponsor (is this scope worth releasing?), customer IT (is this change safe for our environment?) and security (are access controls proven?). The FDE can *stop* any release but *approve* none, which is the clearest single statement of the boundary.
- Capacity cuts landed on the retrieval paths first because each path (API, MCP) multiplies permission-test surface. Cutting a path removes its tests legitimately; cutting tests on a path that still ships does not.
- The research figures (compliance/GRC 48%, OAuth/SSO 43%) are posting mentions, not time spent. I used them only to justify treating access control as core delivery work, not to size effort.
- Follow-up: confirm in discovery that customer IT, not the sponsor, owns change approval at Halyard; if the sponsor does, the deployment row needs revising.
