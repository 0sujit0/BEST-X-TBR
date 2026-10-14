# Therapist flow — agreed 2026-10-14 (D-017, supersedes D-012)

## Dashboard
Today's sessions, uploads pending, summaries to confirm, supervisor notes/tasks.

## Running a session
1. Select scheduled session. Alternative: mark no-show / cancelled with reason → nothing sent to AI.
2. Consent (mandatory, no session without it)
   - Not on file → therapist records it once per patient, uploads signed form
   - Withdrawn → therapist or Org Admin records date; no further sessions
   - Consent does not expire
3. Checklist loads
   - Patient with history → from AI vendor
   - New patient, or AI vendor no response → default checklist for client profile from platform library
4. Session type
   - In person: device synced; device not connected → warning, can continue
   - Online: parent gets one-time guest link by email (no account); recording starts automatically; no live soft alerts
5. Live session
   - Tick checklist items as done (time-stamped); cannot add/remove items; optional reason for unticked items
   - Indicators show data age; device drop → "No data", gap recorded, session continues
   - Soft alerts (in person only) → acknowledge; notes and markers anytime
   - Pause/resume: device data, soft alerts, video paused
   - Online: recording can be paused/resumed separately while call continues
   - Browser closed / connection lost → session keeps running, resumes on reopen
6. End session: manual, scheduled window close, or pause limit reached (pause limit set by BEST Platform Admin). Unacknowledged alerts expire.

## Completing the summary
7. In person: upload transcript from external tool (TXT, PDF, DOCX; configurable). Tool is outside the platform.
   - Not uploaded → "Upload pending" + reminder; after configured time (default 24h) only the checklist is sent to AI; summary labeled "No transcript"
8. Online: recording saved automatically; no upload.
9. Optional attachments (PDF, TXT) after the session only; size limits configurable.
10. Sent to AI vendor: device data, checklist, notes/markers, transcript or recording, attachments → "Summary generating".
11. Draft returned → review (AI-generated label) → edit and confirm. Failed → retry (no limit) or write manually.
12. Confirmed summary saved and locked; corrections as dated addendum. Supervisors see confirmed summaries only.

## Session statuses
Scheduled → In progress ⇄ Paused → Ended → Upload pending → Summary generating → Draft ready / Generation failed → Confirmed. Also: No-show, Cancelled.

## Parked (other roles, not yet changed)
- Org Admin client flow still records consent (D-014) — conflicts with therapist-recorded consent; to resolve when Org Admin flow is revisited.
- Platform Admin: pause limit setting; library of client profiles and default checklists (owner assumed BEST).
- Supervisor: whether checklist, transcript/recording and attachments are shown.
- AI vendor API contract (checklist + summary); screen list.
