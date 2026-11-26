# Forward Deployed Engineering in Practice (course repo)

Course portfolio: the learner acts as the embedded engineer for **Halyard Freight** (fictional mid-sized freight forwarder), delivering **Ask Halyard** (assistant that answers sales & operations staff questions w/ the current, approved answer & its source, showing each person only what they may see). Output is Markdown documents only; no application code.

## Naming
- Never name the repo owner in repo content. Refer to the creator/author/editor as "the engineer" or "the embedded engineer"; use "embedded engineer" in place of "FDE" in artefacts & evidence.
- Third person everywhere in repo docs (README, artefacts, evidence): "the embedded engineer", never "I/my/me".
- Exempt: git commit author/identity, the GitHub username in URLs, verbatim course text in `docs/sources/` & `docs/glossary.md`, published titles & quoted course text containing "FDE".

## Course compliance & flagging (every change, every module)
- Every edit must follow all course conventions, rules & expectations in `docs/sources/` (exercise steps, "Done When", evidence template, labels, commit/tag routine).
- Flag to the engineer (don't silently resolve), each w/ assumptions & a recommendation:
  - <85% confident what the course means (ambiguous wording, vague generalisations, two course passages that disagree).
  - The course, an evidence file or a repo change contradicts anything already in `docs/sources/`, `docs/business-context.md`, `docs/glossary.md`, CLAUDE.md or committed artefacts from earlier modules.
  - A change the engineer requests would fail a module's expected outcome or "Done When" item; name the failing item.
- At the start of each module & before tagging: check every committed exercise of that module against its saved source text; report failures as flags.

## Reference files
- `docs/sources/NN-module-folder-name.md`: each module's course text saved verbatim (wording unchanged; Markdown structure restored). Add one per module when the engineer supplies it. Gitignored (local reference only, never published); never link to it from committed docs. Never save quiz questions or answers.
- `docs/evidence-labels.md`: the course's evidence labels (confidence level of each statement) & usage rules; add new or changed labels per module w/ module citation; flag conflicts. Every artefact line carries a label from the set allowed for that module, formatted `(label)` at line end.
- `docs/business-context.md`: append course-supplied facts about Halyard (company, people, systems, problem, scope), one line each w/ module citation. Duplicate or contradictory context → list under "Open conflicts" & flag; never merge silently.
- `docs/glossary.md`: append every key term & inline definition from each module, verbatim w/ module citation. Use it as the criteria when checking later modules' questions & requests (a request using a term differently from its glossary meaning → flag). A redefined term keeps both entries & is flagged.

## Deliverables (course outcome)
- 14 documents (module 01 table): 01 `engagement-charter.md`, `role-boundaries.md`; 02 `discovery-canvas.md`, `discovery-question-log.md`; 03 `data-inventory.md`, `decomposition-memo.md`; 04 `eval-plan.md`; 05 `production-readiness-plan.md`, `adr/0001-permission-aware-policy-pilot.md`; 06 `demo-script.md`, `limitations-statement.md`; 07 `handover-pack.md`, `runbook.md`, `expansion-recommendation.md`. Plus 1 evidence file per exercise.
- Module 01 (reworked 2026-11-26 to current course text; committed & tagged `module-01` locally; push pending): `docs/engagement-charter.md`, `docs/role-boundaries.md`.
- On completion the engineer submits the repo URL.

## Repository rules (from course instructions)
- Repo: public, named `forward-deployed-engineering-in-practice`, default branch `main`. All course work lives here.
- README: short course description & how to review/run the project. Keep it accurate: reviewers clone, check out each tag `module-01` → `module-07`, read evidence files & follow the README index to each document. Only committed & pushed work is credited.
- Generated code, config & docs live in the repo, built up module by module.

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
- Push only w/ the engineer's explicit permission each time.
- Run `gitleaks git . --no-banner` & `gitleaks dir . --no-banner` before every push (repo safety habit, not a module 01 requirement).

## Secrets & data (public repo)
- Never commit secrets, tokens, `.env` files w/ real values, account identifiers, or client code/data. Use placeholders & `.env.example`.
- All company, people & data are fictional. A fictitious title is fine; an invented approval is not.

## Content rules (from course instructions)
- Labels: use only the evidence labels in `docs/evidence-labels.md` allowed for the current module (module 01: `(assumption)`, `(approval pending)`); supplied-vs-added origin goes in the evidence file Results.
- Never put content from modules not yet saved in `docs/sources/` into committed files.
- Approvals: never claim an approval that was not given; record "approval pending". Separate the person doing work (Responsible) from the person authorised to approve it (Accountable).
- Evaluation is designed during discovery & runs throughout; never postpone it to launch.
- Shrinking scope (e.g. capacity halves): keep the user outcome, narrow the workflow, never silently remove permission/leak tests; tell the sponsor what was cut.
- Recommend a non-AI option (search, deterministic report, policy clean-up) when it solves the problem better.

## Environment & versions
- This course: Git, a Markdown editor & a browser (gitleaks as a repo habit). No npm, GPU, cloud subscription or paid model API.
- Follow-on courses: `data-ingestion-and-etl-pipelines` (source plan → pipeline), `evaluating-and-operating-ai-systems` (implements the eval contract).

## Writing conventions for repo docs
- British English; YYYY-MM-DD; no em dashes.
- Markdown tables are allowed in repo artefacts (responsibility matrices, registers); the no-tables rule applies to chat replies only.
