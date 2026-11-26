# Halyard Freight business context

Supplied facts about the fictional client, collected from the course text saved locally in `docs/sources/` (gitignored). Each line cites its module. Only course-supplied context goes here; the engineer's own assumptions stay in the artefacts that make them. Duplicate or contradictory context is listed under [Open conflicts](#open-conflicts) for the engineer to resolve, not silently merged.

## Company
- Halyard Freight is a fictional mid-sized freight forwarder. (module 01)
- The client, people and numbers are invented. (module 01)

## Problem
- Halyard's guidance is spread across shared folders, a customer records system and old support tickets. (module 01)
- Staff find several versions of the same policy and cannot tell which is current, so they interrupt a colleague to ask. (module 01)

## Request
- The sponsor has asked for Ask Halyard, an assistant that answers staff questions. (module 01)

## Goal
- A member of Halyard's sales or operations staff asks a question and gets the current, approved answer, with its source, without seeing anything they are not allowed to see. (module 01)
- Current and approved: the answer comes from the version a named owner has approved. (module 01)
- With its source: every answer shows the document and page it came from. (module 01)
- Only what they may see: sales staff never see legal documents, not even a title. (module 01)
- Honest when it cannot answer: it says "I cannot answer from your sources" instead of guessing. (module 01)

## Users
- Sales and operations staff. (module 01)

## Scope
- Out of scope: the first release answers questions and changes nothing. It gives no legal advice and takes no action on shipments. (module 01)
- The engineer does not build Ask Halyard; the course produces documents that take it from a vague request to a plan a customer could approve, release safely and hand to another team. (module 01)

## How Ask Halyard works (intended design)
- The system knows who is asking and searches only the documents that person may see. (module 01)
- Passages found: a model writes an answer from those passages only and lists its sources. (module 01)
- Nothing found: it abstains and points to an owner. (module 01)
- Search unavailable: degraded mode; it says so and offers a human fallback. (module 01)

## Decision rights stated by the course
- Customer security approves source access. (module 01)
- The operations lead accepts production use. (module 01)
- The embedded engineer's part is to prove that the access rules are enforced on every search. (module 01)

## Open conflicts

None.
