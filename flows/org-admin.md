# Org Admin flows — agreed 2026-10-12 (D-014)

## Add a user
1. Invite user (email and role)
2. Seat available? (checked against license at invite)
   - No: seats full → ask BEST Platform Admin to add seats (no self-serve)
3. User accepts invite and sets password (MFA mandatory only for Org Admin and BEST roles)
4. Account active; seat is consumed on acceptance (pending invites don't use a seat)

## Add a client
1. Add client (profile and location)
2. Record signed consent (parent signs with clinic staff)
3. Consent recorded? (wearable and telehealth)
   - No: client still gets a care team; sessions are manual-only, telehealth blocked
4. Assign care team (therapist and supervisor)
5. Schedule sessions — Org Admin, in-app or CSV import

## Also covered by PRD (not drawn)
- Deactivating a user frees their seat
- Archiving a client hides them from active workflows
- Withdrawing consent makes later sessions manual-only and blocks telehealth
