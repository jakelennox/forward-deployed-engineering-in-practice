# Ask Halyard role boundaries

Who does the work (Responsible) and who approves it (Accountable) for the five activities in the [engagement charter](engagement-charter.md). Job titles are fictitious; no approval below has happened, so every row is approval pending.

| Activity | Responsible (does the work) | Accountable (approves) | Status |
|---|---|---|---|
| Discovery | Embedded engineer interviews staff, keeps the question log, times the baseline and drafts the evaluation questions | Sponsor (Head of Operations) | Approval pending |
| Source approval | Embedded engineer prepares the access request for each source; each source owner confirms which version is current | Customer security (IT Security Manager) | Approval pending |
| Deployment | Embedded engineer prepares the release and its evidence; customer IT (Infrastructure Lead) makes the change | Customer IT (Infrastructure Lead), with customer security able to block on access grounds | Approval pending |
| Incident response | Embedded engineer pauses the affected path and gathers evidence; customer IT restores infrastructure | Customer security for access-control incidents; operations lead for service incidents (one per incident, never both) | Approval pending |
| Acceptance | Embedded engineer presents the evidence; operations SME (Senior Operations Coordinator) scores the question set | Operations lead (Operations Process Manager) | Approval pending |

## Duties that remain with customer security and operations

- Customer security: granting and revoking source access; defining who may see what; leading access-control incidents; signing off that permission tests cover every user group before each release. (approval pending)
- Operations: naming source owners and resolving conflicting versions; accepting production use; providing SME time for the question set; owning the service after handover. (approval pending)
- Embedded engineer, by contrast: does the work and produces the evidence; can stop a release on a failed gate but approves none. (approval pending)

## Tensions

- Sponsor wants speed: pushes against the Evidence gate line (release before SME review and leak tests finish); customer security decides, and the permission tests are not waived. (assumption)
- Legal wants confidentiality: pushes against the First users line (keep sales off until legal documents, titles included, are proven hidden from them); customer security decides. (assumption)
- Operations wants reliability: pushes against the Outcome line (a speed measure can reward fast but wrong answers); the operations lead decides at acceptance. (assumption)

## Capacity reduction

If delivery capacity halves, the user outcome stays (a current, approved, cited answer, faster than today) for a narrower workflow. The embedded engineer stops these first, in order: (approval pending)

1. Old support tickets as a source: the most version-mixed material and the most likely to hold customer details. (approval pending)
2. The customer records system as a source: the pilot answers from approved policies in shared folders only. (approval pending)
3. Sales staff onboarding: operations staff pilot first; sales follow once their access rules are mapped and tested. (approval pending)
4. Polish: answer formatting and usage reporting beyond what the evidence gate needs. (approval pending)

What stays, unchanged: (approval pending)

- Permission tests for every user group in the pilot, including checks that legal documents and their titles stay hidden. (approval pending)
- The SME-reviewed question set and expected behaviour. (approval pending)
- A citation on every answer, or abstention. (approval pending)
- The degraded-mode message with a human fallback when search is unavailable. (approval pending)
- The escalation line: an access-control failure pauses the release. (approval pending)

The reduced scope goes to the sponsor for sign-off; nothing is cut silently. If the narrower scope still cannot meet the date, the date moves, not the permission tests. (approval pending)
