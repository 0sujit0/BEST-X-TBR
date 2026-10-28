# D-020: Document consolidation and consent recorder

- **Date:** 2026-10-28
- **Phase:** Definition
- **Status:** Active
- **Owner:** Sujit
- **Supersedes:** D-014 and D-017 in part (who records consent)

## Decision
1. Documents are brought back in line now (PRD v3.1, FSD v0.3, flow notes, permission catalogue). Items still awaiting the client are written in, clearly marked "Pending client confirmation".
2. A client's signed consent can be recorded or renewed by the therapist or the Org Admin. Withdrawal likewise.
3. Items settled in the 22 Oct review and FSD discussions go in as agreed: active users instead of seats; MFA mandatory for admin access, optional per user otherwise; password re-entry for critical admin actions; view-only access incl. client details with grey screen for an inactive licence; US formats as configurable lists; design rules (blue/white/green, Poppins, trends with detail on hover); attachments PDF/text/JPG/video; notes typed on screen; one role per user, custom roles (D-019); MongoDB with shared collections.
4. Pending client confirmation: therapist flow changes (consent validity per item, pause as marker, audio via device API with manual trigger, summary not editable, blocking assessment with type set at client setup), KAM-only onboarding with temporary passwords, role-first user creation without per-user permission changes, scheduler vs BCBA as session creator.

## Rationale
Tracker of 28 Oct found 16 documents and 19 conflicts; Sujit chose to update now with pending items marked.

## Revisit Trigger
Client feedback on the pending items.
