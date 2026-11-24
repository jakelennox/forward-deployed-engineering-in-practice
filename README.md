# Forward Deployed Engineering in Practice

Portfolio repository for the *Forward Deployed Engineering in Practice* course. I act as the embedded forward deployed engineer (FDE) for **Halyard Freight**, a fictional mid-sized freight forwarder, and own the delivery of **Ask Halyard**: a permission-aware knowledge assistant for sales and operations staff, with citations, an HTTP API, an MCP server and, later, a small model that summarises support tickets.

This course produces delivery artefacts (Markdown), not an implemented assistant. Implementation follows in later courses.

> All company, people and data in this repository are fictional. No secrets, tokens, account identifiers or real client material are committed.

## Artefacts

| Module | Artefact | Status |
|---|---|---|
| 01 | [Engagement charter](docs/engagement-charter.md) | Draft v0.1, sponsor approval pending |
| 01 | [Role boundaries](docs/role-boundaries.md) | Draft v0.1, approvals pending |
| 02+ | Discovery canvas, data inventory, decomposition memo, 20-question evaluation plan, production readiness plan, trade-off ADR, demo script, operational handover pack | Not started |

## Repository conventions

- Evidence for each exercise: `docs/NN-module-name/exercise-name.md`, started from [docs/evidence-template.md](docs/evidence-template.md) (Goal, Steps taken, Commands, Results, Observations).
- Commits: one or more per exercise; messages start with the module folder name, e.g. `01-the-forward-deployed-engineer-role: ...`.
- Module snapshots: git tag `module-NN` on the last commit of each module.

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

External research inputs (FDE Skills Report 2026, AI Engineer Insights "Forward-Deployed AI Engineer" July 2026, InterviewBit "Forward Deployed Engineer Skills" 2026) are cited as supplied by the course synthesis. Everything about Halyard Freight is a fictional assumption introduced for the exercises and is labelled as such in each artefact.
