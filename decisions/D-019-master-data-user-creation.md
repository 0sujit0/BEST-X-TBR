# D-019: Master data for user creation

- **Date:** 2026-10-28
- **Phase:** Definition
- **Status:** Active
- **Owner:** Sujit
- **Supersedes:** D-016 in part (Supervisor + Org Admin view switch)

## Decision
1. One clinic per user account.
2. One role per user; the same role applies at all of the user's locations (locations only limit which clients and sessions they see).
3. A person with supervisor and admin duties gets a combined custom role (e.g., "Clinical Director"). The Supervisor/Org Admin view switch from D-016 is dropped; permission ACC-05 removed.
4. Several certifications per user, each with its own number, expiry and history.
5. Updates BEST makes to predefined roles apply to all clinics automatically.
6. Licence: a new record for each renewal or plan change; history kept; one active at a time.
7. Clinic user fields can apply to all users or to chosen roles.
8. True master data for user creation: Organization, Location, Role, Permission catalogue, Role–permission mapping, Certification type, Clinic user field, Licence. Never hard-deleted (retired/closed); every change audit-logged.

## Rationale
Confirmed by Sujit 2026-10-28 while defining master data ahead of the schema.

## Revisit Trigger
Client review of FSD v0.3 / RBAC list from BEST.
