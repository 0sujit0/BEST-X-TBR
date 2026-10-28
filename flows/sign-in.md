# Sign-in and routing — agreed 2026-10-12 (D-016), updated 2026-10-28 (D-019, D-020, FSD v0.3)

## First login (new user)
1. Welcome email: login ID (email), temporary password (valid 72 h, configurable), login link
2. Enter ID and temporary password → valid and in time? No → error / expired (admin re-sends)
3. Set new password (policy: 12+ chars, upper, lower, number, symbol; not last 5)
4. MFA required? → enter email code
5. Licence active? → home screen with permitted modules, else restricted mode

## Later logins
1. Login screen (no user-type choice); Forgot password → reset link (30 min)
2. Credentials valid? No → error; locks after 5 failures until reset
3. Account deactivated? → access denied, contact clinic admin
4. MFA required? Mandatory for any role with admin access (Users & roles or Clinic settings); optional per user otherwise, set by the Org Admin → 6-digit email code (10 min)
5. Licence active? No → view-only access incl. client details; grey screen + "License inactive · View only" label
6. Home screen shows only permitted modules; auto-logout after 15 min idle (warning at 13)

## Routing
- By role to its home screen. One role per user (D-019); the Supervisor/Org Admin view switch is removed — a person with both duties gets a combined custom role.
- BEST staff use the separate back-office portal.
