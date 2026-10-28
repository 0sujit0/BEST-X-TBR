# D-021: Permission model for roles

- **Date:** 2026-10-28
- **Phase:** Definition
- **Status:** Active (TBR position; awaiting BEST confirmation)
- **Owner:** Sujit
- **Supersedes:** FSD v0.2/v0.3 module-level permission grid (None / View / Edit per module)

## Decision
1. Role only: a user's access comes only from their role; no per-user permission changes (FSD BR-07).
2. Custom roles are built by ticking individual permissions from the catalogue, grouped by module, with "Select all" per module and a scope (Own, Assigned, Clinic) per ticked permission (FSD v0.4 S4, BR-26).
3. 14 modules: My account (always on), Dashboard, Sessions, Summaries, Supervision, Clients, Assessments, Consent, Devices, Reports, Users & roles, Clinic settings, Audit log, Support access. Sujit had no preference on adding Supervision, Devices and Support access; TBR recommendation (add all three) taken.
4. Org Admin role gets session scheduling only (SES-01 to SES-05); session records stay hidden.

## Rationale
Answers to the four FSD open points on 28 Oct. Permission ticks match the 86-permission catalogue and the MongoDB schema (roles.permissions with permissionId and scope); module-level settings could not express some agreed defaults. Scheduling-only access reconciles D-014 with "no clinical data for Org Admin".

## Revisit Trigger
BEST feedback on FSD v0.4; Adithya's RBAC list; confirmation of who creates sessions (Scheduler or BCBA).
