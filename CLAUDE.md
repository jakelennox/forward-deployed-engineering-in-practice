# Forward Deployed Engineering in Practice (course repo)

Course portfolio: the learner acts as embedded FDE for **Halyard Freight** (fictional mid-sized freight forwarder), delivering **Ask Halyard** (permission-aware knowledge assistant for sales & ops; citations, HTTP API, MCP server, later a small ticket-summarisation model). Output is Markdown delivery artefacts, not an implemented assistant.

## Deliverables (course outcome)
- Discovery canvas; data inventory; decomposition memo; 20-question evaluation plan; production readiness plan; trade-off ADR; demo script; operational handover pack.
- Module 01 (done): `docs/engagement-charter.md`, `docs/role-boundaries.md`.
- Final module ends with a submission checklist exercise; learner submits the repo URL.

## Repository rules (from course instructions)
- Repo: public, named `forward-deployed-engineering-in-practice`, default branch `main`. All course work lives here.
- README: short course description & how to review/run the project. Keep it accurate: reviewers clone, check out each tag `module-01` → `module-07`, read evidence files & run the project from the README. Only committed & pushed work is credited.
- Generated code, config & docs live in the repo, built up module by module.
- Halyard generator (if used): copy `scripts/generate-halyard.ts` & previous course code **into** this repo (never a git submodule), or regenerate with `HALYARD_SEED=20261103`. Never publish generated personal-looking data.

## Evidence files
- Path: `docs/NN-module-name/exercise-name.md` (e.g. `docs/01-the-forward-deployed-engineer-role/map-role-boundaries.md`).
- Start each from a copy of `docs/evidence-template.md`.
- Exactly 5 headings, in this order: `## Goal`, `## Steps taken`, `## Commands`, `## Results`, `## Observations` (under a `# Exercise title` H1).
- Keep every heading even if short; write "None" rather than deleting a section.
- Commands: paste real commands copied from the terminal. Results: paste real output (trim long logs to the lines that matter); never describe output instead of showing it.
- Screenshots, code, scripts & diagrams referenced by an evidence file are committed next to it in the same commit.
- Reasoning a reviewer would ask about goes under Observations; explanations only count as evidence when written down.

## Commits, tags & pushes
- 1+ commits per exercise; every message starts with the module folder name, e.g. `01-the-forward-deployed-engineer-role: add engagement charter`.
- At the end of each module: tag the module's final commit `module-NN` (zero-padded, `module-01` … `module-07`) & push it: `git push origin module-NN`. Check w/ `git ls-remote --tags origin`.
- Workflow (`~/Dev/CLAUDE.md` rule: branch before committing on the default branch): commit on a branch named after the module folder; fast-forward `main` once the module is done; tag the commit on `main`.
- Push only w/ Jake's explicit permission each time.
- Run `gitleaks git . --no-banner` & `gitleaks dir . --no-banner` before every push (course requires it before final submission).

## Secrets & data (public repo)
- Never commit secrets, tokens, `.env` files w/ real values, account identifiers, or client code/data. Use placeholders & `.env.example`.
- All company, people & data are fictional. A fictitious title is fine; an invented approval is not.

## Content rules (from course instructions)
- Label sources: separate supplied facts (course brief), external research findings & fictional Halyard assumptions introduced by the learner. Charter convention: `[F]` fact, `[A]` assumption, `[D]` decision proposal.
- Research inputs: FDE Skills Report 2026 (117 postings, 78 companies), AI Engineer Insights "Forward-Deployed AI Engineer" (July 2026), InterviewBit "Forward Deployed Engineer Skills" (2026). Stats come from the course synthesis, not a reproducible census. Posting frequencies are mentions, not time spent or a competency ranking, & they don't sum to 100; they support directional priorities only.
- Approvals: never claim an approval that was not given; record "approval pending". Separate the person doing work (Responsible) from the person authorised to approve it (Accountable).
- Evaluation is designed during discovery & runs throughout; never postpone it to launch.
- Shrinking scope (e.g. capacity halves): keep the user outcome, narrow the workflow, never silently remove permission/leak tests; tell the sponsor what was cut.
- Each workflow stage (discovery → feasibility → proof of concept → production → evaluations & monitoring → handover & expansion) needs a decision & evidence. A prototype proves a bounded hypothesis; production adds identity, resilience, observability & ownership.
- Recommend a non-AI option (search, deterministic report, policy clean-up) when it solves the problem better.
- Describe capabilities & constraints rather than claiming a version number guarantees correctness.

## Environment & versions
- This course: Git, a Markdown editor, a browser & gitleaks only. No npm, GPU, cloud subscription or paid model API.
- Shared implementation baseline (context for planning only, not installed; verified 2026-11-03): Node.js 26 LTS, npm 11, TypeScript 7.0.2; PostgreSQL 18 + pgvector 0.8.7; Ollama 0.40.14 w/ `qwen3.5:4b`; `qwen3-embedding:0.6b` (1024 dims); DuckDB 2.0.0 via `@duckdb/node-api@2.0.0-r.1`, DuckLake 1.0. TypeScript-first; Python only for ecosystem-specific data/model tooling.
- Follow-on courses: `data-ingestion-and-etl-pipelines` (source plan → pipeline), `evaluating-and-operating-ai-systems` (implements the eval contract).

## Writing conventions for repo docs
- British English; YYYY-MM-DD; no em dashes.
- Markdown tables are allowed in repo artefacts (responsibility matrices, registers); the no-tables rule applies to chat replies only.
