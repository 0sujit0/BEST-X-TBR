# Current State

> Rewritten by the Chief PM at the end of every session. Keep under ~800 words.
> When it crosses that, closed items move to `archive/`.

**Last session:** 2026-10-28
**Current phase:** Definition — PRD consolidated (v3.1); first FSD (user creation and login) in review
**Phase started:** TBC

## Top Priorities
<!-- Max 3. Each with owner and due date. -->
1. Send PRD v3.1, FSD v0.4 and the permission catalogue to BEST; get confirmation on the pending items in PRD Appendix A.2 — Owner: Sujit — Due: TBC
2. Once confirmed, retire or rebuild the 14 Oct therapist and onboarding Word docs from PRD §7.2 / §7.5 — Owner: Sujit — Due: TBC
3. Refresh BEST_Open_Questions.xlsx from PRD Appendix A.2 — Owner: Sujit — Due: TBC

## Open Questions
> Full options, trade-offs and recommendations: `open-questions.md`. 18 open, 10 block PRD sign-off (⚑).

**⚑ First to close:** Q-01 in-session experience · Q-02 regulatory pathway · Q-03 wearable · Q-07 pilot customer and scope

| ID | Question | ⚑ | Sessions untouched |
|---|---|---|---|
| Q-01 | In-session experience — TBR position D-001, awaiting BEST | ⚑ | 0 |
| Q-02 | Regulatory pathway — closed: no counsel, wearable category internal (D-011) | | 0 |
| Q-03 | Wearable selection and child tolerance | ⚑ | 0 |
| Q-04 | North Star Metric — parked (D-007), revisit before pilot | | 0 |
| Q-05 | Timeline structure | | 0 |
| Q-06 | Stakeholders and decision rights | ⚑ | 0 |
| Q-07 | Pilot customer (scope settled TBR-side, D-002) | ⚑ | 0 |
| Q-08 | Meaning of "clinical decision making (basic)" — TBR position D-006 | ⚑ | 0 |
| Q-09 | AI scope in MVP — TBR position D-005 | ⚑ | 0 |
| Q-10 | Consent for child data and AI training — TBR position D-006 | ⚑ | 0 |
| Q-11 | SpO₂ and "stress" wording — TBR position D-006 | | 0 |
| Q-12 | Telehealth in MVP — TBR position D-004 | ⚑ | 0 |
| Q-13 | Scheduling source — proposed: Scheduler or BCBA, pending client | | 0 |
| Q-14 | Org Admin access to clinical data — none by default; combined custom role if needed (D-019) | | 0 |
| Q-15 | Break-glass access rules | | 0 |
| Q-16 | Licensing ownership — closed: Platform Admin maintains licensing table (D-010) | | 0 |
| Q-17 | Values for placeholder thresholds — TBR position D-006 | ⚑ | 0 |
| Q-18 | Platform Admin vs SRE split | | 0 |
| Q-19 | Supervisor documentation approval scope | | 0 |

## Blockers & Risks
| Item | Impact | Owner | Mitigation |
|---|---|---|---|
|  |  |  |  |

## Next Actions
| Action | Owner | Due | Status |
|---|---|---|---|
| Share PRD v3.1 + diagrams, FSD v0.4, permission catalogue | Sujit | TBC | Ready |
| Collect client answers on pending items (consent validity, pause, audio and recording, AI summary, assessments, session creation, onboarding, per-user permissions, module list) | Sujit | TBC | Open |
| Update design mocks to FSD v0.4: S12 Roles list, "Start from", permission ticks with scope | TBR design | TBC | Open |
| Merge Adithya's RBAC list into the permission catalogue when received | Sujit | TBC | Waiting |
| Reflect D-022 master data in PRD §8.12/§8.13, catalogue and schema (kept open) | Sujit | TBC | Open |
| Track drift in docs/BEST_Document_Alignment_Tracker.xlsx | Sujit | Ongoing | Open |

## Commitments Made
<!-- Never compressed. Promises to stakeholders, dates, targets. -->
-

## Changes Since Last Session
<!-- 2–4 lines. Full detail lives in the git commit. -->
- Since 14 Oct: therapist feedback rounds (15, 18, 22 Oct drafts, with client), KAM-only onboarding, user creation and login FSD (v0.1 → v0.3), permission catalogue, role-first user creation, master data (D-019), MongoDB schema.
- 28 Oct consolidation (D-020): PRD v3.1 with 11 redrawn figures and Appendix A; FSD v0.3 (role-first, S12 Roles list, BR-20–25); catalogue now 86 permissions (ACC-05 removed); alignment tracker shows 25 topics, 12 awaiting client, none unreflected.
- Consent is recorded or renewed by the therapist or Org Admin (D-020).
- FSD open points answered (D-021): role only; roles built from permission ticks with scope; 14 modules; Org Admin schedules sessions only. FSD v0.4 issued.
- Master data for the rest of the platform decided (D-022); not yet reflected in PRD, catalogue or schema.
