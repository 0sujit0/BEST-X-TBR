# Open Questions

> Full entries for every open question: options, trade-offs and the Chief PM's recommendation.
> `state.md` carries only the one-line index. When a question is answered, it becomes a decision in `decisions/` and its entry here is marked **Closed → D-0XX**.
> Recommendations are proposals only. Nothing here is decided until Sujit approves it.
>
> ⚑ = blocks PRD sign-off · Baseline: *BEST PRD – Final Rollout* (unrevised as of 2026-10-08)

**Last updated:** 2026-10-09

## Index

| ID | Question | ⚑ | Owner | Depends on | Status |
|---|---|---|---|---|---|
| Q-01 | What does the therapist see during a session — live indicators, alerts, or nothing? | ⚑ | BEST + TBR | Q-02, Q-03 | TBR position → D-001; awaiting BEST |
| Q-02 | What is the regulatory pathway — is any part of this an FDA medical device? | ⚑ | BEST | — | Open |
| Q-03 | Which wearable, and is it tolerable and accurate for these children? | ⚑ | BEST + TBR | Q-01 | Open |
| Q-04 | What is the North Star Metric? | ⚑ | BEST + TBR | Q-01 | Parked → D-007 |
| Q-05 | How should the delivery timeline be structured? | | TBR | Q-01, Q-07 | Open |
| Q-06 | Who are the named stakeholders and who decides what? | ⚑ | BEST + TBR | — | Open |
| Q-07 | Who is the pilot customer, and how much commercial scope does the pilot need? | ⚑ | BEST | — | Scope → D-002; pilot customer still open |
| Q-08 | What does "clinical decision making (basic)" mean? | ⚑ | BEST | Q-02 | TBR position → D-006; awaiting BEST |
| Q-09 | How much AI is in the MVP? | ⚑ | BEST + TBR | Q-02 | TBR position → D-005; awaiting BEST |
| Q-10 | Who gives consent for the child's data, and does it cover AI training? | ⚑ | BEST | — | TBR position → D-006; awaiting BEST |
| Q-11 | Keep SpO₂ and the word "stress"? | | BEST + TBR | Q-02 | TBR position → D-006; awaiting BEST |
| Q-12 | Is telehealth in the MVP? | ⚑ | BEST | Q-03, Q-10 | TBR position → D-004; awaiting BEST |
| Q-13 | How do session schedules get into the platform? | | BEST | — | Open |
| Q-14 | Can Organization Admins see clinical session data? | | BEST | — | Open |
| Q-15 | How does emergency (break-glass) access to PHI work? | | BEST + TBR | — | Open |
| Q-16 | Who owns plans and entitlements — Finance or Platform Admin? | | BEST | — | Open |
| Q-17 | What are the actual values behind "sustained", "≥ N sessions", "acceptable latency"? | ⚑ | BEST | Q-01 | TBR position → D-006; awaiting BEST |
| Q-18 | Should Platform Admin and SRE be separate roles? | | TBR | — | Open |

---

## Q-01 · In-session experience: live indicators and alerts ⚑
**Owner:** BEST + TBR · **Raised:** 2026-10-02 · **Depends on:** Q-02, Q-03
**PRD refs:** §3, §8.5, §8.6, §11 (soft alerts in MVP) vs §19.5 (never trigger alerts or prompts during live sessions)

**Why it matters:** The single biggest driver of scope, regulatory risk, device choice and timeline. The PRD contradicts itself.

| Option | What it means | Gains | Costs |
|---|---|---|---|
| **A. Post-session only** | In session: notes, markers, device status. All wearable data shown afterwards on a timeline aligned to markers. | Lowest regulatory exposure. Periodic sync (§8.4) is enough, so wider vendor choice. Simplest build, no alert tuning. Cleanly tests whether therapists value the data at all. | Drops the §2 promise of "awareness during sessions". Value arrives only after the session. BEST may see it as diluted. Least differentiated. |
| **B. Live indicators, no alerts** | §8.5 rising / stable / settling indicators. No push alerts. | Keeps live awareness, therapist stays in control. | Still real-time interpretation of continuous signals — in the FDA's watch zone. Needs a latency target and fast-syncing vendor; a stale "stable" is a trust problem. Real-time age-aware baselines (§5.2) are real engineering. Therapist attention is on the child, not the screen. |
| **C. Indicators + soft alerts (PRD as written)** | §8.5 + §8.6 in full. | The full vision. Strongest differentiation. | Highest regulatory risk — pushing an alert about a child to a clinician is the clearest step toward device classification. Liability for false or missed alerts. Tightest latency. Needs validated wearables. §19.5 contradiction must be resolved. |

**Note:** the options are layers — B builds on A, C on B. A-first then cleared for C loses time, not work. C-first then refused means rebuilding the in-session experience.

**Chief PM recommendation:** A for MVP; B and C gated on counsel's opinion (Q-02). If BEST says live awareness is the reason they're buying, B with counsel fast-tracked in parallel.
**Ask BEST:** Is live in-session awareness the core reason for this product, or are documentation and supervisor visibility the main value?

---

## Q-02 · Regulatory pathway and FDA classification ⚑
**Owner:** BEST · **Raised:** 2026-10-02
**PRD refs:** §5, §14, §19 (all written to stay non-diagnostic)

**Why it matters:** FDA's January 2026 CDS guidance keeps software that analyses signals or patterns from continuous measurements, or makes time-sensitive outputs, under oversight. Wellness positioning requires no disease or clinical-management claims — hard for a clinical tool used in autism therapy.

| Option | Gains | Costs |
|---|---|---|
| **A. Written opinion from FDA regulatory counsel before building in-session features** | Authoritative answer. Protects BEST and TBR. Cheap relative to rework. | Takes weeks. Counsel cost (budget is confidential — Sujit to confirm). |
| **B. FDA Pre-Submission (Q-Sub) meeting** | Answer from FDA itself. | Months, not weeks. Only worth it if counsel says it's a grey zone. |
| **C. Proceed on internal interpretation** | No delay. | Full regulatory risk sits with BEST, and with TBR's delivery. Not defensible if challenged. |

**Chief PM recommendation:** A now; B only if counsel flags a grey zone. Build Option A of Q-01 while waiting. *Not legal advice — this is the product call pending counsel.*

---

## Q-03 · Wearable selection and validation ⚑
**Owner:** BEST + TBR · **Raised:** 2026-10-02 · **Depends on:** Q-01
**PRD refs:** §8.4 (vendor-agnostic, read-only, consent-based, periodic sync), §17.2 (over-reliance on wearables)

**Why it matters:** Sensory-sensitive children may refuse to wear devices. Consumer readings in children can be unreliable. Vendor must sign a BAA (§15.1). Sync interval determines whether "live" is possible.

| Option | Gains | Costs |
|---|---|---|
| **A. Pick one vendor now** | Fastest to integrate. | Single point of failure. May not suit every child. |
| **B. Vendor-agnostic layer + tolerance test of 2 shortlisted devices** | Matches §8.4. Real evidence from children before commitment. | A few weeks of testing at a BEST clinic. Needs consent for the test. |
| **C. Defer devices — manual-only MVP** | No device risk at all. | Removes the core differentiator. Barely a product. |

**Shortlist criteria:** signs a BAA · API data access · sync interval · child comfort and wear-time · data gaps · cost.
**Chief PM recommendation:** B. If Q-01 lands on A, sync interval stops being a hard criterion.

---

## Q-04 · North Star Metric ⚑
**Owner:** BEST + TBR · **Raised:** 2026-10-08 · **Depends on:** Q-01
**PRD refs:** §10 (metrics listed, no targets or baselines)

| Option | Gains | Costs |
|---|---|---|
| **A. Weekly active therapists** | Easy to measure. | Measures logins, not value. |
| **B. % of sessions with a therapist-reviewed summary** | Tied to the documentation value. Works under any Q-01 option. | Can be rubber-stamped — needs a guard metric. |
| **C. Documentation time saved per session** | Closest to real value. | Needs a baseline measured before the pilot starts. |
| **D. % of sessions reviewed by a supervisor** | Captures supervisor value. | Secondary — depends on therapists first. |

**Chief PM recommendation:** B as North Star, C as guard metric. Measure the documentation-time baseline before the pilot. Revisit if Q-01 goes to C (then alert relevance matters).

---

## Q-05 · Delivery timeline structure
**Owner:** TBR · **Raised:** 2026-10-08 · **Depends on:** Q-01, Q-07
**Context:** A draft M1–M7 Gantt was produced on 2026-10-05. Treat it as draft until Q-01 and Q-07 close.

| Option | Gains | Costs |
|---|---|---|
| **A. Fixed date, flexible scope** | Predictable for BEST. | Constant scope negotiation. |
| **B. Fixed scope, flexible date** | Complete product. | Unpredictable — risky with regulatory unknowns. |
| **C. Gate-based milestones with target windows** | Honest about unknowns (counsel, device test, pilot results). Clear go/no-go points. | BEST may want hard dates. |

**Chief PM recommendation:** C — gates at counsel opinion, device test, pilot exit.

---

## Q-06 · Stakeholders and decision rights ⚑
**Owner:** BEST + TBR · **Raised:** 2026-10-08

| Option | Gains | Costs |
|---|---|---|
| **A. One accountable product owner at BEST, with a named clinical advisor** | Fast decisions. Clear accountability. | Load on one person. |
| **B. Steering committee** | Broad buy-in. | Slow. Decisions get diluted. |

**Chief PM recommendation:** A, plus a named clinical lead (BCBA) for Q-11 and Q-17 sign-offs.
**Needed:** names on both sides; who signs off PRD and final acceptance.

---

## Q-07 · Pilot customer and commercial scope ⚑
**Owner:** BEST · **Raised:** 2026-10-02
**PRD refs:** §3, §8.9, §8.10, §11 (full licensing, billing, finance console and expense controls in MVP)

**Why it matters:** Admin, billing and back-office requirements outweigh the clinical core. Building all of it before proving therapist value delays learning.

| Option | Gains | Costs |
|---|---|---|
| **A. Full SaaS shell in MVP (PRD as written)** | Sellable from day one. | Heaviest build. Clinical validation comes last. |
| **B. Pilot in BEST's own clinics; minimal org admin; defer billing, payments, finance console, expense controls** | Fastest to clinical value. | Commercial launch later. Architecture must still be multi-tenant from day one. |
| **C. Multi-tenant + org admin + licensing; defer billing and payments** | Ready for a first external customer without the finance stack. | Middle on both. |

**Chief PM recommendation:** B if the pilot is BEST's own clinics; C if it's a paying external organisation.
**Ask BEST:** Who is the pilot customer, and what result decides go / no-go?

---

## Q-08 · "Clinical decision making (basic)" ⚑
**Owner:** BEST · **Raised:** 2026-09-29 · **Depends on:** Q-02
**PRD refs:** §3 and §11 (in MVP) vs §5.1 (no clinical recommendations), §13.2 (no automated decision making)

| Option | Gains | Costs |
|---|---|---|
| **A. Remove the phrase** | Removes the contradiction and a regulatory red flag. | None, if it never meant anything specific. |
| **B. Redefine as "structured observation and documentation support"** | Keeps intent in safe language. | Needs BEST to confirm that's what they meant. |
| **C. Keep as written** | — | Undefined, contradictory, and a gift to a regulator. |

**Chief PM recommendation:** A or B. Ask BEST what they intended.

---

## Q-09 · AI scope in the MVP ⚑
**Owner:** BEST + TBR · **Raised:** 2026-09-29 · **Depends on:** Q-02
**PRD refs:** §14.2 (MVP: trend highlighting, cross-session comparison, adaptive alert tuning) vs §11 (pattern detection is Phase 2) vs §19 (unphased)

| Option | Gains | Costs |
|---|---|---|
| **A. Summary drafting only** | Lowest risk. Directly cuts documentation effort. | Less "AI" to show. |
| **B. A + post-session pattern prompts (§19)** | Distinctive insight. | Patterns need ≥ N completed sessions per child — little to show early in a pilot anyway. |
| **C. Full §14.2 including adaptive alert tuning** | Full vision. | Only meaningful if Q-01 = C. Highest risk. |

**Chief PM recommendation:** A for MVP; B in Phase 2 once enough sessions exist, matching §11.

---

## Q-10 · Consent for the child's data and AI training ⚑
**Owner:** BEST · **Raised:** 2026-10-02
**PRD refs:** §8.4 (consent-based), §14.4 (BEST historical data may train AI), §20.6 (telehealth consent). Parents are listed as non-users (§4). No consent store is specified.

| Option | Gains | Costs |
|---|---|---|
| **A. Consent captured outside the app; admin attests in-app** | Uses BEST's existing intake process. | Weak audit trail. |
| **B. Digital consent captured at client onboarding by Org Admin, stored in an in-app consent store** | Auditable, timestamped, role-linked (as §20.6 requires). | Needs a consent-store feature the PRD doesn't define. |
| **C. Per-session consent by therapist** | Very granular. | Heavy friction every session. |

**Chief PM recommendation:** B, with separate opt-ins for AI training and telehealth. Needs BEST's legal review.

---

## Q-11 · SpO₂ and "stress" language
**Owner:** BEST + TBR · **Raised:** 2026-10-08 · **Depends on:** Q-02
**PRD refs:** §8.4 (collects SpO₂), §8.5 (never displays it), §8.8 ("stress trends" in summary)

| Option | Gains | Costs |
|---|---|---|
| **A. Drop SpO₂ from MVP; rename "stress trends" → "heart rate trends"** | Data minimisation. Removes a clinical-sounding claim. | Loses a signal BEST may want later. |
| **B. Collect SpO₂ but don't display; keep "stress"** | Keeps data for later. | Collecting PHI with no use. "Stress" reads as interpretation. |

**Chief PM recommendation:** A. Clinical lead to confirm wording.

---

## Q-12 · Telehealth in the MVP ⚑
**Owner:** BEST · **Raised:** 2026-09-29 · **Depends on:** Q-03, Q-10
**PRD refs:** §20.3 (in MVP) vs §11 (not in phasing). At home, someone must put the wearable on the child — but parents are non-users.

| Option | Gains | Costs |
|---|---|---|
| **A. Full telehealth in MVP** | Matches §20. | Video vendor with BAA, consent flow, home device handling. Big scope add. |
| **B. Telehealth MVP without wearables (manual notes and markers only)** | Simple. §20.5 already makes signal overlays optional. | Less data in remote sessions. |
| **C. Phase 2** | Keeps the MVP focused. | Delays a modality BEST may need. |

**Chief PM recommendation:** C, or B if BEST already runs remote sessions at volume.

---

## Q-13 · Session scheduling source
**Owner:** BEST · **Raised:** 2026-09-29
**PRD refs:** §8.2 ("Session scheduling (scheduling Dept)") — no integration defined

| Option | Gains | Costs |
|---|---|---|
| **A. Integrate with BEST's existing scheduling system** | No double entry. | Depends on that system having an API. |
| **B. CSV import** | Cheap. | Manual and error-prone. |
| **C. Manual entry in-app** | Simplest. | Duplicate work for the scheduling team. |

**Chief PM recommendation:** C or B for pilot, A later.
**Ask BEST:** What system does the scheduling department use today?

---

## Q-14 · Organization Admin access to clinical data
**Owner:** BEST · **Raised:** 2026-10-02
**PRD refs:** §15.3, §18.2 (scope is "own organization" — clinical data not addressed)

| Option | Gains | Costs |
|---|---|---|
| **A. No clinical access by default** | Least privilege. | Admin can't help with clinical queries. |
| **B. Read-only summaries** | Some oversight. | More PHI exposure. |
| **C. Full access** | Simple. | Violates least privilege. |

**Chief PM recommendation:** A — clinical access only if the person also holds a clinical role.

---

## Q-15 · Break-glass access to PHI
**Owner:** BEST + TBR · **Raised:** 2026-10-02
**PRD refs:** §8.10, §15.3, §18.3 (reason, approval, scope, expiry, audit — but no approver or limits named)

| Option | Gains | Costs |
|---|---|---|
| **A. BEST security lead approves** | Fast. | Customer has no say. |
| **B. Customer Org Admin approves** | Customer control. | Slow in an incident. |
| **C. Dual approval; customer notified; short time-box** | Strongest governance. | Slightly slower. |

**Chief PM recommendation:** C, subject to what customer BAAs allow.

---

## Q-16 · Ownership of plans and entitlements
**Owner:** BEST · **Raised:** 2026-10-02
**PRD refs:** §8.10 (Platform Admin manages plans) vs §18.2 (Finance manages plans; Platform Admin manages entitlements)

| Option | Gains | Costs |
|---|---|---|
| **A. Split as §18.2: Finance owns plans and pricing, Platform Admin owns entitlements and config** | Separation of duties. | Needs a hand-off between teams. |
| **B. Single owner** | Simple. | Weaker controls. |

**Chief PM recommendation:** A, with each side approving the other's changes that affect them.

---

## Q-17 · Placeholder thresholds ⚑
**Owner:** BEST · **Raised:** 2026-09-29 · **Depends on:** Q-01
**PRD refs:** "sustained trends" (§8.6), "≥ N sessions" (§19.8), "minimum session count" (§19.7), "acceptable latency" (§9)

**Why it matters:** A vendor can't build or test against words.

| Option | Gains | Costs |
|---|---|---|
| **A. Fix values in the PRD now** | Testable. | Hard to get right before real data. |
| **B. Configurable parameters with defaults signed off by BEST's clinical lead, tuned in pilot** | Testable and adjustable. | Needs a governance step for changes. |
| **C. Leave to the developers** | — | Clinical decisions made by engineers. |

**Chief PM recommendation:** B.

---

## Q-18 · Platform Admin vs SRE
**Owner:** TBR · **Raised:** 2026-10-02
**PRD refs:** §8.10 (separate permission profiles) vs §18.2 (one combined role)

| Option | Gains | Costs |
|---|---|---|
| **A. Separate roles** | Least privilege; matches §8.10. | One more role to manage. |
| **B. Combined (as §18.2)** | Simpler for a small team. | Broad standing access. |

**Chief PM recommendation:** A.
