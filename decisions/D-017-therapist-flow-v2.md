# D-017: Therapist flow revised (team feedback)

- **Date:** 2026-10-14
- **Phase:** Definition
- **Status:** Active
- **Owner:** Sujit
- **Supersedes:** D-012

## Decision
Therapist flow as in `flows/therapist.md`. Changes from D-012:
1. Consent recorded by the therapist, once per patient; mandatory — the manual-only path is removed.
2. Activity checklist: from AI vendor based on patient history; new patient or no response → profile default from platform library. Tick only, time-stamped.
3. Pause/resume session: device data, soft alerts and video pause. Auto-end at pause limit set by BEST Platform Admin.
4. Online sessions: parent joins via one-time guest link; recorded automatically; recording can be paused separately.
5. In person: transcript upload (from external tool) after the session. If missing → reminder; after 24h (configurable) only the checklist goes to AI, summary labeled "No transcript".
6. Attachments (PDF, TXT) after the session only; sent to AI.
7. Defaults accepted: no-show/cancel, device-drop handling, session resume, consent withdrawal, summary locked with addendum, dashboard contents, session statuses, configurable file limits.

## Rationale
Internal team feedback (Priyanshu and team) shared 2026-10-14; clarifications confirmed by Sujit.

## Impacts (parked — therapist scope only for now)
- Conflicts with D-014: Org Admin currently records consent.
- New Platform Admin settings: pause limit, profile/checklist library.

## Revisit Trigger
Org Admin/supervisor flow revision, AI vendor API contract, or BEST feedback.
