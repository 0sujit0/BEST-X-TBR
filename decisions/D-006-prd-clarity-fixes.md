# D-006: PRD clarity and compliance fixes

- **Date:** 2026-10-09
- **Phase:** Definition
- **Status:** Active — proposed; pending BEST confirmation
- **Owner:** Sujit
- **Supersedes:** —
- **Closes:** Q-08, Q-10, Q-11, Q-17 (TBR side)

## Decision
1. Remove "clinical decision making (basic)" from §3 and §11 (Q-08).
2. Drop SpO₂ from MVP; rename "stress trends" to "heart rate trends" in §8.8 (Q-11).
3. Replace placeholder thresholds ("sustained", "≥ N sessions", "acceptable latency", "minimum session count") with configurable parameters whose defaults are signed off by BEST's clinical lead and tuned in the pilot (Q-17).
4. Add a consent store: digital consent captured at client onboarding, with separate opt-ins for AI training and telehealth (Q-10).

## Rationale
Removes contradictions and clinical-sounding claims, makes requirements testable, and fills a compliance gap the PRD references but never defines.

## Revisit Trigger
BEST's clinical lead or legal review asks for a different approach.
