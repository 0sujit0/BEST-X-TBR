# D-015: BEST Back Office flows agreed (license lifecycle, break-glass)

- **Date:** 2026-10-12
- **Phase:** Definition
- **Status:** Active
- **Owner:** Sujit
- **Supersedes:** —

## Decision
Flows as in `flows/back-office.md`. New rules this adds to PRD v3.0:
1. Org Admins get an expiry warning before the license end date (configurable, default 30 days).
2. Expired or suspended license: no new sessions; log-in and viewing of records still allowed; no data deleted.
3. Break-glass: BEST security approves first, then clinic Org Admin; unanswered requests lapse and count as denied.

## Rationale
Derived from PRD v3.0 §8.10, §8.11; confirmed by Sujit.

## Revisit Trigger
BEST feedback on approval order or expiry behaviour.
