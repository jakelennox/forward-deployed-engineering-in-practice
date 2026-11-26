# Write the Engagement Charter

## Goal
Turn the sponsor's vague request for Ask Halyard into a one-page, nine-line charter with a measurable outcome, exclusions, decision rights and a stop condition, where every line is labelled as an assumption or as approval pending.

## Steps taken
1. Created the public repository with a [README](../../README.md), a [.gitignore](../../.gitignore) and the [evidence template](../evidence-template.md) copied from module 01.
2. Wrote [docs/engagement-charter.md](../engagement-charter.md) from the course starter, keeping its nine lines and rewriting all of them; Outcome now says how the reduction is measured without a number.
3. Labelled every line `(assumption)` or `(approval pending)`, as defined in [docs/evidence-labels.md](../evidence-labels.md).
4. Wrote one sponsor objection against a boundary and a reply that keeps the permission gate (below).

## Commands
~~~bash
git init -b main
git switch -c 01-the-forward-deployed-engineer-role
git add README.md .gitignore docs/evidence-template.md docs/engagement-charter.md docs/01-the-forward-deployed-engineer-role/write-the-engagement-charter.md
git commit -F -   # "01-the-forward-deployed-engineer-role: add repo scaffold and engagement charter"
git branch main 01-the-forward-deployed-engineer-role
git switch main
gh repo create jakelennox/forward-deployed-engineering-in-practice --public --source . --remote origin
git push origin main
# rework to the current module 01 text
git switch -c 01-the-forward-deployed-engineer-role
git add .gitignore CLAUDE.md README.md docs/business-context.md docs/glossary.md docs/evidence-labels.md docs/engagement-charter.md docs/01-the-forward-deployed-engineer-role/write-the-engagement-charter.md
git commit -F -   # "01-the-forward-deployed-engineer-role: rework engagement charter to nine labelled lines"
git switch -c 01-the-forward-deployed-engineer-role
git add -A
git commit -F -   # "01-the-forward-deployed-engineer-role: add review index, label formatting and provisional evidence rules"
~~~

## Results
Artefact: [docs/engagement-charter.md](../engagement-charter.md).

Where each line comes from (supplied by module 01, or added by the embedded engineer):

- **Sponsor**: the sponsor's request is supplied; the title and authority are the engineer's assumption.
- **Engineer**: the role is supplied; the limits (no access grants, no acceptance) follow the module's statement that those decisions belong to the customer.
- **Outcome**: the problem (staff cannot tell which version is current and interrupt a colleague) is supplied; the measure is the engineer's.
- **First users**: supplied (sales and operations staff).
- **Not in scope**: no shipment actions and no legal advice are supplied; "answers not grounded in an approved source" is the engineer's, from the "honest when it cannot answer" part of the goal.
- **Decision rights**: security approves source access and the operations lead accepts production use are supplied; sponsor scope and source-owner version approval are the engineer's.
- **Evidence gate**: SME review and zero leaks are supplied by the starter; citation-or-abstain and the title-level check come from the goal table.
- **Escalation**: the pause on access-control failure is supplied by the starter; who signs off the fix is the engineer's.
- **Open assumption**: supplied by the starter; the exclusion of ownerless policies is the engineer's.

**Sponsor objection**: "Everyone using this works for Halyard. Showing a sales colleague that a legal document exists, just its title, does no harm. Drop the title check from the permission tests so we can release sooner."

**Reply**: The title check stays. The goal the sponsor asked for says sales staff never see legal documents, not even a title, because a title alone can reveal a dispute, a customer or a contract under review (assumption). The check is part of the zero-leak evidence gate, and a failure pauses the release under the escalation line. To release sooner, the sources can narrow instead: leave legal documents out of the pilot's searchable set until title-level filtering is proven, so both sales and operations staff can still join the pilot, and the title check still runs for every user group. Pilot users do not need legal documents to answer their questions, and legal advice is already out of scope (assumption). Narrowing scope needs the sponsor's sign-off (approval pending); removing the check is not on offer.

## Observations
- *Least sure line*: Outcome. It assumes the time to an approved answer and the interruptions to colleagues can be measured before the pilot. The operations lead could confirm whether staff can be timed on a question set and whether interruptions can be counted.
- Writing the Outcome without a number was harder than writing a target; the measure and its method are fixed now, and the target waits for the baseline.
- The charter will be revised in module 02 once the client brief is read.
