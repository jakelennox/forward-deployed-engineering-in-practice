# Map Role Boundaries

## Goal
Show who does the work and who approves it for discovery, source approval, deployment, incident response and acceptance, without recording any approval that has not happened, and decide what to stop first if delivery capacity halves while keeping the permission tests.

## Steps taken
1. Wrote the five-activity table in [docs/role-boundaries.md](../role-boundaries.md), with a Status column reading "Approval pending" on every row.
2. Listed the [duties that remain with customer security and operations](../role-boundaries.md#duties-that-remain-with-customer-security-and-operations).
3. Added [Tensions](../role-boundaries.md#tensions): for the sponsor, legal and operations, the charter line each pushes against and the accountable role that decides.
4. Added [Capacity reduction](../role-boundaries.md#capacity-reduction): what stops first, in order, and what stays.
5. Ended every duties, Tensions and Capacity reduction line with `(assumption)` or `(approval pending)`, as defined in [docs/evidence-labels.md](../evidence-labels.md).
6. Studying alone, used the request to halve capacity as the self-challenge (below).

## Commands
~~~bash
git add docs/role-boundaries.md docs/01-the-forward-deployed-engineer-role/map-role-boundaries.md
git commit -F -   # "01-the-forward-deployed-engineer-role: add role boundaries and capacity decision"
git push origin main
# rework to the current module 01 text
git add docs/role-boundaries.md docs/01-the-forward-deployed-engineer-role/map-role-boundaries.md
git commit -F -   # "01-the-forward-deployed-engineer-role: rework role boundaries with tensions and capacity reduction"
git switch main
git merge --ff-only 01-the-forward-deployed-engineer-role
git branch -d 01-the-forward-deployed-engineer-role
git tag module-01
~~~

## Results
Artefact: [docs/role-boundaries.md](../role-boundaries.md).

**Self-challenge (sponsor):** "Delivery capacity has halved and the pilot date is fixed. Cut the permission tests for now; they can come back before the wider rollout."

**Response:** The permission tests stay; the workflow narrows instead. The pilot drops old support tickets and the customer records system as sources and answers from approved policies in shared folders only; operations staff pilot first and sales follow once their access rules are tested. That makes the permission test set smaller, but it still covers every user group in the pilot, including the check that legal documents and their titles stay hidden. The user outcome holds for the pilot group: a current, approved, cited answer, faster than today. The reduced scope goes to the sponsor for sign-off (approval pending); if it still cannot meet the date, the date moves.

## Observations
- Hardest to separate: deployment. The embedded engineer prepares the release and could technically push it, customer IT makes and approves the change, the sponsor decides whether the scope is worth releasing and customer security can block it on access grounds. Writing "can stop a release but approves none" for the embedded engineer made the split clear.
- Incident response needed two accountable roles, split by incident type, so that each incident still has exactly one.
- Follow-up: confirm in discovery that customer IT, not the sponsor, approves changes at Halyard.
