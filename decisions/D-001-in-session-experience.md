# D-001: Keep live indicators and soft alerts in the revised PRD, with risks stated

- **Date:** 2026-10-09
- **Phase:** Definition
- **Status:** Active — TBR position for revised PRD; pending BEST confirmation
- **Owner:** Sujit
- **Supersedes:** —
- **Closes:** Q-01 (TBR side; BEST still to confirm)

## Context
Q-01 offered A (post-session only), B (live indicators, no alerts), C (indicators + soft alerts, PRD as written). Chief PM recommended A.

## Decision
Revised PRD keeps option C: §8.5 live trend indicators and §8.6 soft in-app alerts stay in MVP. The PRD will state the risks explicitly and gate the build of in-session alerting on regulatory counsel's opinion (Q-02).

## Rationale
Sujit's call: preserve BEST's original vision in the client-facing document and let BEST make an informed choice with the risks in front of them, rather than TBR cutting scope unilaterally.

## Options Rejected
| Option | Why rejected |
|---|---|
| A. Post-session only | Diverges from BEST's stated vision before BEST has weighed in |
| B. Indicators, no alerts | Same reason; can still be the fallback if counsel advises against alerts |

## Risks to state in the PRD
- Regulatory: real-time interpretation and alerts on continuous signals sit where FDA's Jan 2026 CDS guidance keeps oversight.
- Liability: false or missed alerts.
- Latency: periodic sync (§8.4) may make "live" indicators stale.
- Device: alert quality depends on wearable accuracy and tolerance in children (Q-03).
- §19.5 conflict to be reconciled: AI pattern prompts stay post-session only; §8.6 soft alerts are rule-based and separate.

## Revisit Trigger
Regulatory counsel's opinion (Q-02), or BEST choosing A or B.
