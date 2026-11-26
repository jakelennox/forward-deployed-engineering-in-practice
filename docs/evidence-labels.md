# Evidence labels

How the engineer knows each statement: each label names a kind of evidence and so the confidence a reader can place in it. Halyard is fictional and nothing is built, so every line in an artefact carries one. Label text is verbatim from module 01 of the course.

## Rules

- Never record an approval, test run or measurement that did not happen. (module 01)
- End a labelled line with the label in brackets, lower case, e.g. `(assumption)`, `(approval pending)`. (module 01, Exercise 1)
- Module 01 artefacts use only Assumption and Approval pending; the other labels apply from the module that introduces them. (module 01)
- A later module that adds, renames or changes a label is added here with its module, and any conflict is flagged to the engineer.

## Labels

| Label | Use it when | First used |
|---|---|---|
| Assumption | It is your working guess and needs an owner to confirm it | module 01 |
| Approval pending | A sign-off is needed and has not happened | module 01 |
| Supplied fact | It is stated in the brief or the module text | later module |
| Interview claim | Someone said it in the interview; nobody measured it | later module |
| Decision | It is a choice you recommend, with your reason | later module |
| Planned / not verified | It is designed but not built or tested | later module |
| Requires customer validation | Only the customer's real data or people can confirm it | later module |
| Tabletop | You walked through it on paper with simulated numbers | later module |
| Storyboard | It is a mock-up of a screen or response | later module |

## Provisional rules (pending module 02)

Not stated by the course; proposed by the embedded engineer to fill gaps in module 01. Re-checked against each new module's text; any difference is flagged and the rule updated or dropped.

- **Evidence strength**: supplied fact over interview claim over assumption; where a measured and a claimed figure disagree, the measured one is used and the gap is flagged. Inferred from the label definitions ("nobody measured it"). (assumption)
- **Decision precedence**: the Accountable role for the activity in [role-boundaries.md](role-boundaries.md) decides; the permission gate is never traded for speed or scope (module 01: "the permission tests stay"; the reply "must keep the permission gate"). (assumption)
- **Stakeholder conflicts**: where two stakeholders' claims contradict each other, or a claim contradicts a supplied fact, both sources are recorded and the conflict is flagged to the engineer; neither is chosen silently. (assumption)
- **One label per line**: the most cautious label that applies, e.g. `(approval pending)` over `(decision)` until sign-off happens. (assumption)
