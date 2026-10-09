# D-002: Lean pilot — defer billing and finance from MVP

- **Date:** 2026-10-09
- **Phase:** Definition
- **Status:** Active — proposed in revised PRD; pending BEST confirmation
- **Owner:** Sujit
- **Supersedes:** —
- **Closes:** Q-07 (TBR side; BEST still to confirm pilot customer)

## Context
§3, §8.9, §8.10 and §11 put the full commercial and back-office stack in MVP, outweighing the clinical core.

## Decision
MVP keeps multi-tenant architecture, organization admin, user and client management, and licensing. Billing, invoices, payments, subscription expense controls and the BEST finance console move to a later phase.

## Rationale
Gets to clinical value sooner and tests whether therapists find the product useful before building the full finance stack. Architecture stays multi-tenant so nothing is rebuilt later.

## Options Rejected
| Option | Why rejected |
|---|---|
| Full SaaS shell in MVP | Heaviest build; clinical validation comes last |
| Clinical core only | Licensing and tenant admin are needed even for a pilot across clinics |

## Revisit Trigger
BEST confirms the pilot customer is a paying external organisation that must be invoiced through the platform.
