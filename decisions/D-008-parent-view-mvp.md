# D-008: Parents become users — read-only child history in the MVP

- **Date:** 2026-10-09
- **Phase:** Definition
- **Status:** Active — Sujit's instruction; pending BEST confirmation
- **Owner:** Sujit
- **Supersedes:** — (changes charter "Not users" line and PRD v1 §4, §3, §12, §20.3)

## Decision
Parents / guardians are users. In the MVP they get a read-only web view of their own child's history:
- **What they see:** session list (date, duration, in person / telehealth) and therapist-confirmed summaries. No raw device data, alerts, notes or markers.
- **Release:** a session appears once the therapist confirms its summary; each clinic can require supervisor approval first.
- **Onboarding:** Org Admin invites the guardian recorded in the consent record; MFA on; access ends when consent is withdrawn, the client is archived or the guardian is removed.
- Mobile access comes with the Phase 2 apps.

## Rationale
Sujit's call: parents need visibility of their child's therapy history. Confirmed-summaries-only keeps clinical review in the loop and avoids exposing raw physiological data to non-clinicians.

## Options Rejected
| Option | Why rejected |
|---|---|
| Parent access in Phase 2 | Sujit wants it in the MVP |
| Parent mobile app in MVP | Adds a mobile build to an already heavy MVP |
| Show trend charts / everything | Raw signals and notes invite misreading and raise the clinical-claim risk |
| Release immediately after session | No review step before a parent reads it |
| Self sign-up with clinic code | Weaker identity link to the consenting guardian |

## Risks
Parents misreading summaries; custody / multiple-guardian disputes; summaries edited after release.

## Revisit Trigger
BEST declines parent access, or pilot feedback shows parents need more (or less) detail.
