# Forward Deployed Engineering in Practice

Portfolio repository for the *Forward Deployed Engineering in Practice* course. The embedded engineer works for **Halyard Freight**, a fictional mid-sized freight forwarder, and owns the delivery of **Ask Halyard**: a permission-aware assistant that gives sales and operations staff the current, approved answer with its source, showing each person only what they may see.

This course produces Markdown documents only; there is no application code.

> All company, people and data in this repository are fictional. No secrets, tokens, account identifiers or real client material are committed.

## Review index

Each module's documents and the evidence file for each exercise. Check out the matching tag (`module-01` to `module-07`) to review a module as submitted.

| Module | Exercise | Document | Evidence | Status |
|---|---|---|---|---|
| 01 | Write the Engagement Charter | [Engagement charter](docs/engagement-charter.md) | [write-the-engagement-charter.md](docs/01-the-forward-deployed-engineer-role/write-the-engagement-charter.md) | Draft, sponsor approval pending |
| 01 | Map Role Boundaries | [Role boundaries](docs/role-boundaries.md) | [map-role-boundaries.md](docs/01-the-forward-deployed-engineer-role/map-role-boundaries.md) | Draft, approvals pending |
| 02 to 07 | Not started | Discovery canvas, question log, data inventory, decomposition memo, eval plan, production readiness plan, ADR, demo script, limitations statement, handover pack, runbook, expansion recommendation | Not started | Not started |

Reference documents, updated each module: [Business context](docs/business-context.md), [glossary](docs/glossary.md), [evidence labels](docs/evidence-labels.md); [evidence template](docs/evidence-template.md).

## Repository conventions

- **Evidence for each exercise**: `docs/NN-module-name/exercise-name.md`, started from [docs/evidence-template.md](docs/evidence-template.md) (Goal, Steps taken, Commands, Results, Observations).
- **Commits**: one or more per exercise; messages start with the module folder name, e.g. `01-the-forward-deployed-engineer-role: ...`.
- **Module snapshots**: git tag `module-NN` on the last commit of each module.

## Running the project

There is no application code in this course. To review:

```bash
git clone https://github.com/jakelennox/forward-deployed-engineering-in-practice.git
cd forward-deployed-engineering-in-practice
git tag --list 'module-*'
git checkout module-01
```

Read the Markdown in any editor with preview, or on GitHub. Requirements: Git and a Markdown viewer; no npm, GPU, cloud subscription or paid model API.

## Sources

Everything about Halyard Freight is fictional. Course-supplied context is in [docs/business-context.md](docs/business-context.md); each artefact labels what the embedded engineer assumes and what is still pending approval.
