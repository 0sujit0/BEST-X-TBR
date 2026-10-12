# Sign-in and routing — agreed 2026-10-12 (D-016)

## Sign-in
1. Open web app → login screen
2. Enter email and password (or reset password); first-time users arrive via invite link instead (see Org Admin: adding a user)
3. Credentials valid? No → error; retry or reset. Account locks after repeated failed attempts (configurable, default 5) until password reset
4. MFA required? Org Admin and BEST roles → enter MFA code
5. Account active? No (deactivated) → access denied; contact clinic admin
6. Signed in; session timeout returns to login (§8.1)

## Routing
1. Clinic users: organization license active? No (expired/suspended) → restricted mode, view records only (D-015). BEST staff skip this check
2. Route by role: Therapist → session list; Supervisor → caseload; Org Admin → clinic console; BEST staff → back office
3. Supervisor with Org Admin permission lands on caseload and can switch to the clinic console (single login)
