# D-022: Master data for the rest of the platform

- **Date:** 2026-10-28
- **Phase:** Definition
- **Status:** Active (TBR position; awaiting BEST confirmation)
- **Owner:** Sujit
- **Extends:** D-019 (master data for user creation)

## Decision
Clients, sessions, consent records and assessments are core records, not master data; fixed statuses are coded enums.

| # | Master data | Owner | Rule |
|---|---|---|---|
| 1 | Consent item types | BEST, plus clinic-added items | BEST items (wearable, session audio, telehealth) drive platform blocks; validity set by BEST per clinic. Clinics can add their own items: recorded and tracked for validity with expiry warnings, but never block a session or feature (catalogue SET-05) |
| 2 | Assessment types | BEST, platform-wide | VB-MAPP, ABLLS-R, Vineland with key scores; BEST adds new types on request for all clinics |
| 3 | Assessment validity | Clinic | Each clinic sets its own period freely (catalogue SET-06); default 6 months, warning 30 days before |
| 4 | Client profiles | BEST | Age band + assessment level; needs a level mapping per assessment type |
| 5 | Checklist library | BEST, clinic can copy and adapt | One default checklist per profile; clinic copies are its own; therapists still cannot add or remove items in a session |
| 6 | Device models and registry | BEST | Each device registered to a clinic and location; linked to a session at start and released at end; never tied to a client |
| 7 | Signal types, reference ranges, alert parameters, display phrases | BEST clinical lead only | One signed-off set for all clinics; changes approved and audit-logged |
| 8 | Reason lists (no-show, cancellation, checklist item not done) | BEST defaults, clinic can add | Clinic can add or retire its own reasons; "Other" with free text always available |
| 9 | Client fields | Clinic | Same as clinic user fields (text, number, date, dropdown; optional or mandatory); never sent to the AI service |

## Rationale
Answers to master data questions 1–10 on 28 Oct. Clinical and AI-facing lists stay with BEST for consistency and safety; operational lists can be extended by clinics.

## Open
- Level mapping per assessment type for client profiles (BEST clinical lead).
- Assessment validity set freely by clinics has no minimum; revisit if BEST wants a floor.

## Revisit Trigger
BEST review; clinical lead input on profiles and checklist library.
