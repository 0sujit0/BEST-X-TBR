# Product Charter

> Protected file. The Chief PM may propose changes but never commits them without explicit approval from the owner.
> Keep under ~500 words.

**Status:** DRAFT — pre-filled from prior project context, pending Sujit's approval
**Last approved:** —

## Product
- **Name:** BEST Platform — Therapy Session Monitoring & Clinical Support Platform
- **Client:** BEST (US provider of pediatric ABA / autism therapy)
- **Delivered by:** TBR Consulting (took over delivery from BEST). PM: Sujit
- **One-line description:** A HIPAA-compliant web app that turns wearable data from a child's therapy session into simple trend signals and an AI-drafted session summary for the therapist, wrapped in a multi-clinic SaaS platform.

## Vision
Therapists today rely on memory and manual notes, and wearable data is scattered. BEST Platform gives therapists and supervisors a clear, objective view of each session that supports clinical judgment and never replaces it, and lets BEST sell this as a licensed platform to clinics.

## North Star Metric
- **Metric:** Not yet decided (tracked as open question Q-04)
- **Current value:** —
- **Target & date:** —

## Target Users
| Segment | Core problem | Why they'd choose us |
|---|---|---|
| Therapist (BT) | Tracks a child's state from memory during sessions | Live trend signals, soft alerts, quick notes, auto-drafted summary |
| Supervisor (BCBA) | Reviews sessions across a caseload with thin data | Flagged sessions, trends, timelines to coach therapists |
| Clinic admin | Manages staff, clients, licences and billing | One console per clinic, tenant-isolated |
| BEST internal (platform/SRE, ops, finance) | Runs the platform for many clinics | Health, logs, incidents, billing exceptions |
| Parent / guardian | No visibility into their child's therapy sessions | Read-only view of their child's confirmed session history (D-008) |

**Not users:** children (the child wears the device but never uses the app), insurers. Parents became users on 2026-10-09 (D-008), approved by Sujit.

## Hard Constraints
- **Clinical guardrail:** signals are reference only. No diagnosis, no treatment recommendations, no emergency language. Trends against age-appropriate baselines, not fixed thresholds.
- **Compliance:** HIPAA throughout. BAAs with every vendor handling PHI. Strict tenant isolation. MFA mandatory for admins.
- **Data:** monitoring limited to the session window. Wearable integration vendor-agnostic, read-only, consent-based. Clients archived, never deleted.
- **Alerts:** in-app only, fire on sustained trends, throttled.
- **Platform:** MVP is web-only. Android and iOS in Phase 2.
- **Budget:** Confidential. Not recorded here; the Chief PM should ask Sujit before any cost-sensitive recommendation.
- **Timeline:** Not fixed. To be shaped in Chief PM working sessions (open question Q-05).

## Stakeholders
> Named stakeholders to be added by Sujit.

| Name | Role | What they care about | Decision rights |
|---|---|---|---|
| BEST Product Team | Client | TBC | Final acceptance, PRD scope |
| TBR Consulting | Delivery partner | TBC | TBC |
| Sujit | PM (TBR) | Delivery on scope and compliance | TBC |
