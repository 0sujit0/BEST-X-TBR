# D-016: Sign-in and role routing flow agreed

- **Date:** 2026-10-12
- **Phase:** Definition
- **Status:** Active
- **Owner:** Sujit
- **Supersedes:** —

## Decision
Flow as in `flows/sign-in.md`. New rules:
1. Account lockout after repeated failed logins (configurable, default 5) until password reset.
2. Supervisor with Org Admin permission switches between caseload and clinic console in one login.
3. Expired/suspended license → clinic users sign in to view-only restricted mode; BEST staff unaffected.

## Rationale
Completes the user journey from opening the web app; confirmed by Sujit.

## Revisit Trigger
Security review or BEST feedback.
