# Clinic onboarding flow — agreed 2026-10-14 (D-018)

## Request and approval
1. BEST shares an onboarding link (one per clinic, valid 14 days, re-sendable).
2. Onboarding type selected on the form:
   - Sales-assisted: BEST Key Account Manager fills the form for the clinic
   - Self-onboarding: clinic fills the form itself
3. Form can be saved as draft.
   - Mandatory: legal name, EIN, NPI, address, time zone, contact person, ≥1 location, chosen plan
   - Documents: signed BAA + service agreement mandatory; W-9, state license, insurance optional
   - Duplicate EIN or NPI blocked
4. Submit → BEST Platform Admin reviews: approve / reject with reason / send back (comments shown; unlimited resubmits). Applicant emailed on each outcome.

## Setup and go-live
5. Organization (tenant) and locations created.
6. License created from chosen plan; Platform Admin can adjust seats and dates.
7. BEST configures: telehealth on/off, clinical parameter values; registers BEST-supplied wearables to the clinic.
8. Contact person invited as Org Admin (uses one seat; invite expires 7 days, re-sendable).
9. Org Admin first login (password + MFA) → clinic Active. Until then: Approved.
10. Org Admin uploads consent form template; optional CSV import of staff and clients.

## Clinic statuses
Draft → Submitted → Sent back / Rejected / Approved → Active → Suspended / Expired (follow license).

## New role
BEST Key Account Manager: share links; create, save, submit onboarding requests; no clinical data access.
