# D-012: Therapist user flow agreed

- **Date:** 2026-10-12
- **Phase:** Definition
- **Status:** Active
- **Owner:** Sujit
- **Supersedes:** —

## Decision
Therapist flow as in `flows/therapist.md`. Key rules confirmed:
1. No consent → in-person session runs manual-only; telehealth cannot start.
2. No live soft alerts in telehealth.
3. Session ends manually or automatically at window close; open alerts expire.
4. Failed AI summary → unlimited retry or manual summary.
5. Supervisors see confirmed summaries only.

## Rationale
Derived from PRD v3.0 §8.2, §8.6, §8.8, §8.12, §17; confirmed by Sujit.

## Revisit Trigger
BEST feedback on the flow, or design/UAT findings.
