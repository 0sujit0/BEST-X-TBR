# BEST Platform — User creation and login: mock brief

Version: based on FSD "User Creation and Login" v0.4 (28 October 2026)
Use with: the BEST design rules file (supplied separately)

---

## 1. How to use this brief

You are generating high-fidelity UI mocks for a web application.

- **This file defines what is on each screen:** layout regions, fields, buttons, states, messages and sample data.
- **The design rules file defines how it looks:** colours, typography, spacing, components and visual style. Where this file and the design rules seem to disagree on visual matters, follow the design rules.
- **Do not add fields, buttons, screens or features** that are not in this brief. Do not remove any either. Where something is not specified, keep it minimal and consistent with the other screens.
- **Use only the sample data in Section 9.** It is fictional. Never show real names, real patient data or real email domains.
- Use the exact message text from Section 8 wherever a message appears.
- Use American English and US formats (dates as `Oct 28, 2026`, phone as `(555) 010-0142`).

---

## 2. Product context (for orientation only)

- **Product:** a HIPAA-compliant platform for US clinics that provide ABA therapy to children. It monitors therapy sessions, shows trends from wearables, and produces AI-generated session summaries.
- **This brief covers one module:** how a clinic's Organization Admin creates users and roles, and how users log in.
- **Platform:** web app on desktop and tablet browsers. Design at **1440 × 900** (desktop). Login-type screens (S5–S8) also at **1024 × 768** (tablet).
- **Who uses these screens:**
  - **Organization Admin (Org Admin):** manages users, roles and clinic settings. Has no access to clinical session data.
  - **Clinic users:** therapists, supervisors (BCBAs) and custom roles. They see the login screens and their own home screen.
- **Key concepts:**
  - Each user holds **exactly one role**. Permissions belong to the role, never to the individual user.
  - **Predefined roles** (Therapist, Supervisor, Organization Admin) are maintained by BEST and cannot be edited by the clinic. A clinic can create **custom roles** by ticking permissions, starting blank or from a copy of another role.
  - A role has **admin access** if it includes any permission from the *Users & roles* or *Clinic settings* modules. Users with admin access must enter an emailed code at every login (MFA).
  - The clinic's license has an **active-user limit**. Users with status Invited, Active or Locked count towards it. Deactivated users do not.
  - When the license is inactive (expired or suspended), the app enters **restricted mode**: grey screen, view-only, with a "License inactive · View only" label.

---

## 3. App shell (signed-in screens)

All signed-in screens (S1–S4, S9–S12) share this shell:

- **Header bar** (full width):
  - Left: product name "BEST", then the clinic name "Maple Grove ABA Clinic".
  - Right: signed-in user's name and role ("Sam Brooks · Organization Admin") with an avatar showing initials. Clicking it opens a small menu: My profile, Log out.
- **Left navigation** (clinic console). Show only the modules the signed-in user's role allows. For the Org Admin in these mocks, show:
  - Dashboard
  - Sessions (schedule only)
  - Clients
  - Consent
  - Devices
  - Reports
  - **Users & roles** (expanded, with sub-items **Users** and **Roles**; highlight the current one)
  - Clinic settings
  - Audit log
  - Support access
- **Main content area:** page title, optional breadcrumb, then the screen content.
- **Inactivity warning** (any signed-in screen, as one extra frame): a small dialog after 13 minutes idle: "You'll be logged out in 2 minutes due to inactivity." Buttons: **Stay signed in** (primary), **Log out**.

Login screens (S5–S8) have no shell: a centred card on a plain page with the "BEST" wordmark above it.

---

## 4. Screen map and flow

```
S5 Login ──(first login, temporary password)──► S6 Set new password ──(if MFA required)──► S7 Email code ──► S10 Home
   │                                                       (if no MFA) ───────────────────────────────────► S10 Home
   ├──(later logins)──(if MFA required)──► S7 Email code ──► S10 Home
   └── "Forgot password?" ──► S8 Forgot password ──(reset link in email)──► S6 Set new password ──► S5 Login

S10 Home (Org Admin) ──► S1 Users list ──► "Create user" ──► S2 Details ──► S3 Role ──► (S11 Confirm password, if admin role) ──► back to S1 with message M-16
                              │                                   └── "Create new role" ──► S4 Create role (pop-up)
                              ├── row action Deactivate / Reactivate ──► S9 pop-up ──► S11 Confirm password (deactivate only)
                              └── "Roles" ──► S12 Roles list ──► Create / Copy / Edit ──► S4  ·  Retire ──► confirm or M-18
```

---

## 5. Screens

### S1 — Users list

**Purpose:** all users of the clinic. The starting point for creating, deactivating and reactivating users.
**Breadcrumb:** Clinic console › Users & roles › Users

**Layout, top to bottom:**
1. Page title "Users". On the right: the counter **"Active users: 18 of 25"**, a secondary button **Roles** (opens S12) and a primary button **Create user** (opens S2).
2. Filter row: **Status** dropdown (All, Invited, Invite expired, Active, Locked, Deactivated), **Role** dropdown (All + role names), **Location** dropdown (All + locations), **Search** field (placeholder "Search by name or email").
3. Table with columns: **Name**, **Email**, **Role**, **Location(s)**, **Status** (shown as a status badge), **Last login**, and a **⋯** actions menu per row.
4. Pagination below the table ("1–10 of 24").

**Row actions** (only the ones that apply to the row's status):
- Active or Locked: **Deactivate**
- Deactivated: **Reactivate**
- Invited or Invite expired: **Re-send welcome email**

**States to mock:**
- **S1-a Default:** 10 rows from the sample data (mix of statuses).
- **S1-b Limit reached:** counter reads "Active users: 25 of 25"; **Create user** is disabled; a tooltip on it shows M-04.
- **S1-c Success:** after creating a user, a success message M-16 appears at the top of the page; the new user is in the list with status Invited.
- **S1-d Row menu open:** the ⋯ menu open on an Active user, showing "Deactivate".

---

### S2 — Create user: details (step 1 of 2)

**Purpose:** enter the new user's details.
**Breadcrumb:** Clinic console › Users & roles › Users › Create user
**Step indicator:** "Step 1 of 2 · Details" (step 2 is "Role").

**Fields** (two-column form on desktop; * = mandatory):

| Field | Type | Mandatory | Helper / validation |
|---|---|---|---|
| First name | Text | * | 1–50 characters |
| Last name | Text | * | 1–50 characters |
| Email (login ID) | Email | * | Helper: "This is the user's login ID." Error if already used: M-01 |
| Phone | Phone | — | US format, e.g. (555) 010-0142 |
| Location(s) | Multi-select dropdown | * | At least one. Options: Main, East, North |
| Job title | Text | — | Up to 100 characters |
| **Certifications** (repeatable group) | — | — | Each row has three fields: **Certification type** (dropdown: RBT, BCBA), **Certification number** (text), **Certification expiry** (date picker). Under the rows, a link **"+ Add another certification"**. Each added row has a remove (×) control. |
| Clinic fields | As defined by the clinic | As defined | Section titled "Clinic fields". In the mock show one: **Employee ID** (text, optional). Helper under the section: "Fields for specific roles appear in the next step." |

**Buttons** (bottom right): **Cancel** (secondary), **Next** (primary).

**States to mock:**
- **S2-a Empty:** blank form.
- **S2-b Filled:** filled with sample user Jordan Lee, two certifications (RBT and BCBA rows).
- **S2-c Errors:** first name empty ("Enter a first name."), email showing M-01, no location selected ("Select at least one location.").
- **S2-d Cancel confirmation:** small dialog "Discard this new user? The details you entered will be lost." Buttons: **Keep editing**, **Discard**.

---

### S3 — Create user: role (step 2 of 2)

**Purpose:** choose the user's one role and see what it allows.
**Step indicator:** "Step 2 of 2 · Role".

**Layout:**
1. **Role** dropdown (mandatory, single choice). Grouped options: "Predefined roles" (Therapist, Supervisor, Organization Admin), then "Clinic roles" (Clinical Director, Intake Coordinator). Beside it, a link **"Create new role"** (opens S4).
2. **"What this role can do"** panel (read-only), with the note "Set on the role · read only". It lists each module with how many of its permissions the role includes, for example "Sessions — 15 of 20", or "None" in a muted style. Each module row can be expanded to list the permission names.
3. **Role-specific clinic fields:** appear only when the chosen role has them. In the mock, for Supervisor show one field **"BACB supervisor ID"** (text, optional).
4. **MFA checkbox:** "Require email code at every login (MFA)". Helper: "Always on when the role has admin access."
5. **Admin access notice** (only when the role has admin access): "This user will enter an email code at every login." The MFA checkbox is then ticked and locked.

**Buttons:** **Back** (secondary, returns to S2 with entries kept), **Cancel** (secondary), **Create user** (primary).

**States to mock:**
- **S3-a Therapist selected:** summary shows Therapist counts (Section 10); MFA unticked and editable.
- **S3-b Organization Admin selected:** admin access notice shown; MFA ticked and locked.
- **S3-c Supervisor selected:** role-specific field "BACB supervisor ID" visible.
- **S3-d Expanded module:** in the summary, "Sessions" expanded to show its permission names, with ticks for the ones the role has.

---

### S4 — Create or edit role (pop-up / modal)

**Purpose:** build a custom role by ticking permissions. Opened from S3 ("Create new role") or S12 ("Create role", "Copy", "Edit").

**Fields:**

| Field | Type | Mandatory | Notes |
|---|---|---|---|
| Start from | Dropdown | * (new role only) | "Blank", or "Copy of: [role name]" for any predefined or clinic role. Picking a copy pre-ticks that role's permissions. Hidden when editing an existing role. |
| Role name | Text | * | 2–50 characters; unique in the clinic. Error: M-02 |
| Description | Text area | * | Up to 250 characters |
| Permissions | Tick boxes grouped by module | * | One collapsible group per module (14 modules, Section 10). Each group header has the module name, a **"Select all"** tick box and a counter ("8 of 8 ticked"). Inside, one row per permission: tick box, permission name, short description in muted text, and on ticked rows a **Scope** dropdown (Own, Assigned, Clinic). The **My account** group is always fully ticked and locked. Error if nothing else is ticked: M-03 |

**Buttons:** **Cancel** (secondary), **Save role** (primary).

**States to mock:**
- **S4-a New, blank:** Start from "Blank"; Sessions group expanded with two permissions ticked (SES-01, SES-02, scope "Assigned"); Clients group collapsed with "Select all" ticked ("8 of 8 ticked"); other groups collapsed.
- **S4-b Copy:** Start from "Copy of: Therapist"; name "Senior Therapist"; groups show Therapist counts.
- **S4-c Edit with users:** title "Edit role: Clinical Director" (no Start from field). After pressing Save, a confirmation dialog shows M-20 ("…applies to 2 users…") with buttons **Cancel** and **Save changes**.
- **S4-d Errors:** role name showing M-02; M-03 shown above the permission groups.

---

### S5 — Login

**Layout:** centred card. Title "Log in".
**Fields:** **Email**; **Password** (masked, with Show/Hide).
**Buttons and links:** **Log in** (primary, full width), link **"Forgot password?"**. Small text under the card: "Trouble signing in? Contact your clinic admin."
There is **no user-type or role selector**. The role comes from the account.

**States to mock:**
- **S5-a Default.**
- **S5-b Wrong password:** M-05 shown, with "X" replaced by "3".
- **S5-c Locked:** M-14.
- **S5-d Deactivated account:** M-06.
- **S5-e Temporary password expired:** M-13.

---

### S6 — Set new password

**When shown:** after the first login with a temporary password, and after opening a valid password-reset link.
**Layout:** centred card. Title "Set a new password". Sub-text: "Welcome. Replace your temporary password to continue." (For a reset, the sub-text is "Choose a new password for your account.")
**Fields:** **New password** and **Confirm password** (both masked, with Show/Hide).
**Live checklist** under the fields. Each rule turns complete as it is met:
- At least 12 characters
- Upper and lower case letters
- A number and a symbol
- Not one of your last 5 passwords

**Button:** **Save password** (primary, full width).

**States to mock:**
- **S6-a Partly met:** first two rules complete, last two pending.
- **S6-b Mismatch:** M-09 under Confirm password.
- **S6-c Reused password:** M-08.

---

### S7 — Email code (MFA)

**Layout:** centred card. Title "Enter the code". Text: "We sent a 6-digit code to j•••••@example.com. It expires in 10 minutes."
**Input:** six single-digit boxes.
**Button:** **Verify** (primary, full width).
**Resend:** text "Didn't get it? You can resend the code in 0:42", which becomes a link **"Resend code"** after 60 seconds.

**States to mock:**
- **S7-a Default:** three digits entered.
- **S7-b Wrong code:** M-10.
- **S7-c Expired code:** M-11.
- **S7-d Resend available:** the "Resend code" link is shown.

---

### S8 — Forgot password

**Layout:** centred card. Title "Forgot password". Text: "Enter your email and we'll send you a reset link."
**Field:** **Email**.
**Button:** **Send reset link** (primary). Link: "Back to log in".

**States to mock:**
- **S8-a Default.**
- **S8-b Submitted:** M-12 shown. Show the same message whether or not the email exists.
- **S8-c Link expired** (reached from an old link): M-15, with a button **Request a new link**.

---

### S9 — Deactivate and reactivate (pop-ups)

**Deactivate:**
- Title: "Deactivate Jordan Lee?"
- Text: "This user will not be able to log in. Their records are kept and they no longer count as an active user."
- Buttons: **Cancel**, **Deactivate**. Pressing Deactivate opens S11.

**Reactivate:**
- Title: "Reactivate Jordan Lee?"
- Text: "This user will be able to log in again and will count as an active user."
- Buttons: **Cancel**, **Reactivate**.

**States to mock:**
- **S9-a Deactivate pop-up.**
- **S9-b Reactivate pop-up.**
- **S9-c Reactivate blocked:** M-04 in the pop-up; Reactivate disabled.
- **S9-d Last admin:** deactivating the only user who can manage users shows M-07; Deactivate disabled.

---

### S10 — Home screen states

- **S10-a Normal (Org Admin):** a simple home page in the shell. Title "Good morning, Sam". Four summary cards: "Active users 18 of 25", "Invited 3", "Locked 1", "License ends Oct 31, 2027". Plus a short "Recent activity" list (user created, role edited, user deactivated) with dates.
- **S10-b Restricted mode (Therapist):** the same shell turned grey.
  - Header label in the centre: **"License inactive · View only"**.
  - Signed in as "Alex Rivera · Therapist". Left nav: Home, My sessions, Clients, Summaries.
  - Text: "You can view records, including client details. Starting sessions and making changes is paused until your clinic's license is renewed."
  - A "Today's sessions" list with two rows. Each row has **View record** enabled and **Start session** disabled.

---

### S11 — Confirm password (pop-up)

**When shown:**
- before deactivating a user;
- before creating a user whose role has admin access;
- before saving a new or edited role that includes Users & roles or Clinic settings permissions.

**Layout:**
- Title: "Confirm it's you".
- Text naming the action, e.g. "Enter your password to deactivate Jordan Lee."
- Field: **Password** (masked, with Show/Hide).
- Buttons: **Cancel**, **Confirm**.

**States to mock:**
- **S11-a Default.**
- **S11-b Wrong password:** M-17.

---

### S12 — Roles list

**Purpose:** see the clinic's roles; set roles up before creating users (optional).
**Breadcrumb:** Clinic console › Users & roles › Roles
**Header:** title "Roles", primary button **Create role** (opens S4 with Start from "Blank").

**Table columns:**
- Role
- Type (badge: Predefined or Custom)
- Users (count)
- Admin access (Yes / No)
- Actions

**Actions per row:**
- Predefined roles: **View**, **Copy**.
- Custom roles: **Edit**, **Copy**, **Retire**.

**Note** under the table: "Predefined roles are maintained by BEST. A custom role can be retired only when no user holds it."

**States to mock:**
- **S12-a Default:** rows from Section 9.
- **S12-b Retire blocked:** retiring "Clinical Director" shows M-18 in a dialog with one button **OK**.
- **S12-c Retire allowed:** retiring "Intake Coordinator" (0 users) shows a confirmation dialog: "Retire Intake Coordinator? It will no longer be offered when creating users." Buttons: **Cancel**, **Retire**.
- **S12-d Saved:** after an edit, M-19 appears at the top of the page.

---

## 6. Account statuses (for badges in S1)

| Status | Meaning |
|---|---|
| Invited | Created; first login not done; temporary password still valid (72 hours) |
| Invite expired | Temporary password expired before first login |
| Active | Has logged in and can log in |
| Locked | Blocked after 5 failed attempts until the password is reset |
| Deactivated | Blocked by the Org Admin; records kept; does not count towards the limit |

---

## 7. Rules the mocks must respect

1. One role per user; there is no per-user permission editing anywhere.
2. The login screen never asks for a user type or role.
3. Admin access forces MFA; the MFA checkbox is locked on in that case.
4. Create user is blocked when the active-user limit is reached.
5. The last user who can create users cannot be deactivated.
6. A custom role in use cannot be retired; predefined roles cannot be edited or retired.
7. Restricted mode is view-only, including client details; all edit actions are disabled.
8. Passwords, temporary passwords and codes are never displayed in full anywhere.

---

## 8. Messages (use this exact text)

| ID | When | Text |
|---|---|---|
| M-01 | Email already used | An account with this email already exists. |
| M-02 | Role name already used | A role with this name already exists. Choose a different name. |
| M-03 | No permission ticked | Tick at least one permission for this role. |
| M-04 | Active-user limit reached | Your license's active-user limit has been reached. Ask BEST to raise it. |
| M-05 | Wrong email or password | Email or password is incorrect. X attempts left before your account is locked. |
| M-06 | Deactivated user logs in | Your account is not active. Please contact your clinic admin. |
| M-07 | Last user who can manage users | This user cannot be deactivated. The clinic needs at least one user who can manage users. |
| M-08 | Password fails policy or reused | Your password does not meet the requirements shown. |
| M-09 | Passwords do not match | Passwords do not match. |
| M-10 | Wrong email code | The code is incorrect. Check the latest email and try again. |
| M-11 | Email code expired | This code has expired. Request a new code. |
| M-12 | Forgot password submitted | If an account exists for this email, we have sent a password reset link. |
| M-13 | Temporary password expired | Your temporary password has expired. Ask your clinic admin to send a new one. |
| M-14 | Account locked | Your account is locked after too many attempts. Use Forgot password to reset it. |
| M-15 | Reset link expired or used | This link has expired. Request a new password reset link. |
| M-16 | User created | User created. A welcome email has been sent to [email]. |
| M-17 | Wrong password in S11 | Password is incorrect. Try again. |
| M-18 | Retire a role that users hold | This role is held by X users. Move them to another role before retiring it. |
| M-19 | Edited role saved | Role saved. X users with this role now have the updated access. |
| M-20 | Before saving an edit to a role in use | This change applies to X users who hold this role. Continue? |

M-01 to M-17 are errors or warnings; M-16 and M-19 are success messages; M-20 is a confirmation.

**Illustrative wording (not in the FSD message list).** The following texts are placeholders written for the mocks. Use them as given, but treat them as draft copy to be confirmed:
- inline field errors in S2-c;
- the cancel dialog (S2-d) and the reactivate and retire dialogs (S9-b, S12-c);
- the reset sub-text in S6 and the "Request a new link" button in S8-c;
- the inactivity warning;
- the home-page cards in S10-a.

---

## 9. Sample data (fictional — use only this)

**Clinic:** Maple Grove ABA Clinic · Locations: Main, East, North · License: 25 active users, ends Oct 31, 2027
**Signed-in Org Admin:** Sam Brooks (s.brooks@example.com)

**Users (S1):**

| Name | Email | Role | Location(s) | Status | Last login |
|---|---|---|---|---|---|
| Alex Rivera | a.rivera@example.com | Therapist | Main | Active | Today, 9:12 AM |
| Jordan Lee | j.lee@example.com | Supervisor | Main, East | Invited | — |
| Morgan Patel | m.patel@example.com | Therapist | East | Locked | Oct 26, 2026 |
| Sam Brooks | s.brooks@example.com | Organization Admin | Main | Active | Today, 8:40 AM |
| Taylor Chen | t.chen@example.com | Clinical Director | Main, North | Active | Yesterday |
| Casey Nguyen | c.nguyen@example.com | Therapist | North | Invite expired | — |
| Riley Adams | r.adams@example.com | Therapist | Main | Active | Today, 7:55 AM |
| Jamie Ortiz | j.ortiz@example.com | Supervisor | East | Active | Oct 27, 2026 |
| Drew Kim | d.kim@example.com | Intake Coordinator | Main | Deactivated | Sep 30, 2026 |
| Avery Brown | a.brown@example.com | Therapist | East | Active | Today, 10:03 AM |

**Roles (S12):**

| Role | Type | Users | Admin access |
|---|---|---|---|
| Therapist | Predefined | 11 | No |
| Supervisor | Predefined | 4 | No |
| Organization Admin | Predefined | 1 | Yes |
| Clinical Director | Custom | 2 | Yes |
| Intake Coordinator | Custom | 0 | No |

**New user in S2/S3:** Jordan Lee · j.lee@example.com · (555) 010-0142 · Main, East · Job title "Lead BCBA" · Certifications: BCBA 1-23-45678, expires Mar 31, 2028; RBT RBT-0099123, expires Jun 30, 2026 · Employee ID E-104

---

## 10. Modules and permissions (for S3 and S4)

Permission counts for predefined roles:

| Module | Total | Therapist | Supervisor | Org Admin |
|---|---|---|---|---|
| My account | 5 | 5 (always on) | 5 (always on) | 5 (always on) |
| Dashboard | 4 | 2 | 2 | 1 |
| Sessions | 20 | 15 | 7 | 5 (scheduling only) |
| Summaries | 4 | 4 | 1 | None |
| Supervision | 7 | 1 | 6 | None |
| Clients | 8 | 1 | 2 | 8 |
| Assessments | 4 | 2 | 4 | 1 |
| Consent | 4 | 4 | 1 | 4 |
| Devices | 2 | 1 | None | 2 |
| Reports | 4 | None | 2 | 1 |
| Users & roles | 11 | None | None | 11 |
| Clinic settings | 9 | None | None | 9 |
| Audit log | 2 | None | None | 1 |
| Support access | 2 | None | None | 2 |
| **Total** | **86** | **35** | **30** | **50** |

Permission names by module (use these labels in S3 expanded rows and S4):

| Module | Count | Permissions |
|---|---|---|
| My account | 5 | ACC-01 Log in and log out; ACC-02 Change or reset own password; ACC-03 Enter email code at login; ACC-04 View own notifications; ACC-05 View own profile and permissions |
| Dashboard | 4 | DSH-01 View therapist dashboard; DSH-02 View caseload dashboard; DSH-03 View organization dashboard; DSH-04 View trends with detail on hover |
| Sessions | 20 | SES-01 View session schedule; SES-02 Create a session; SES-03 Reschedule or edit a session; SES-04 Cancel a session or mark a no-show; SES-05 Bulk import sessions (CSV); SES-06 Start an in-person session; SES-07 Start an online session; SES-08 Pause and resume a session; SES-09 Pause and resume the call recording; SES-10 End a session; SES-11 Tick checklist items; SES-12 Add notes, observations and markers; SES-13 Acknowledge soft alerts; SES-14 Create tasks and follow-ups; SES-15 Add attachments; SES-16 Generate summary without audio; SES-17 View session record; SES-18 Open attachments and recordings; SES-19 Download attachments and recordings; SES-20 Watch a live session in progress |
| Summaries | 4 | SUM-01 View AI summary; SUM-02 Add therapist note to the summary; SUM-03 Retry summary generation; SUM-04 Write the summary manually |
| Supervision | 7 | SPV-01 View flagged sessions; SPV-02 Compare sessions side by side; SPV-03 Mark a session reviewed; SPV-04 Add a note or task for a therapist; SPV-05 Remind a therapist; SPV-06 Approve clinical documentation; SPV-07 View notes and tasks from the supervisor |
| Clients | 8 | CLI-01 View client list and profiles; CLI-02 Create a client; CLI-03 Edit a client profile; CLI-04 Archive a client; CLI-05 Restore an archived client; CLI-06 View archived clients; CLI-07 Assign or reassign the care team; CLI-08 Bulk import clients (CSV) |
| Assessments | 4 | ASM-01 View assessments and scores; ASM-02 Upload assessment report and key scores; ASM-03 Select the assessment type for a client; ASM-04 Correct or replace an assessment entry |
| Consent | 4 | CON-01 View consent status and records; CON-02 Record signed consent; CON-03 Renew an expired consent item; CON-04 Record consent withdrawal |
| Devices | 2 | DEV-01 View the clinic’s devices; DEV-02 Assign a device to a client or session |
| Reports | 4 | RPT-01 View client trend reports; RPT-02 View therapist and caseload reports; RPT-03 View organization usage reports; RPT-04 Export reports |
| Users & roles | 11 | USR-01 View the user list and active-user count; USR-02 Create a user; USR-03 Give a user admin access; USR-04 Turn MFA on or off for a non-admin user; USR-05 Edit a user’s details or role; USR-06 Deactivate a user; USR-07 Reactivate a user; USR-08 Re-send the welcome email; USR-09 Create a custom role; USR-10 Edit or retire a custom role; USR-11 View role definitions |
| Clinic settings | 9 | SET-01 View clinic settings; SET-02 Edit organization profile and time zone; SET-03 Manage locations; SET-04 Manage clinic fields for user creation; SET-05 Manage clinic consent items; SET-06 Set the assessment validity period; SET-07 Set session defaults; SET-08 Set notification preferences; SET-09 View license details |
| Audit log | 2 | AUD-01 View the audit log; AUD-02 Export the audit log |
| Support access | 2 | SUP-01 Approve or decline BEST support access; SUP-02 View support access history |

Show the permission ID in small muted text before each name (for example "SES-02 · Create a session").

---

## 11. Frames to produce

| # | Frame | Size |
|---|---|---|
| 1 | S1-a Users list | 1440 × 900 |
| 2 | S1-b Limit reached | 1440 × 900 |
| 3 | S1-c Success after create | 1440 × 900 |
| 4 | S1-d Row menu open | 1440 × 900 |
| 5 | S2-a Details, empty | 1440 × 900 |
| 6 | S2-b Details, filled with two certifications | 1440 × 900 |
| 7 | S2-c Details, errors | 1440 × 900 |
| 8 | S2-d Cancel confirmation | 1440 × 900 |
| 9 | S3-a Role: Therapist | 1440 × 900 |
| 10 | S3-b Role: Organization Admin (MFA locked) | 1440 × 900 |
| 11 | S3-c Role: Supervisor with role-specific field | 1440 × 900 |
| 12 | S3-d Role summary, module expanded | 1440 × 900 |
| 13 | S4-a Create role, blank | 1440 × 900 |
| 14 | S4-b Create role, copy of Therapist | 1440 × 900 |
| 15 | S4-c Edit role, M-20 confirmation | 1440 × 900 |
| 16 | S4-d Create role, errors | 1440 × 900 |
| 17 | S5-a Login | 1440 × 900 and 1024 × 768 |
| 18 | S5-b to S5-e Login errors | 1440 × 900 |
| 19 | S6-a Set new password, partly met | 1440 × 900 and 1024 × 768 |
| 20 | S6-b, S6-c Password errors | 1440 × 900 |
| 21 | S7-a Email code | 1440 × 900 and 1024 × 768 |
| 22 | S7-b to S7-d Code states | 1440 × 900 |
| 23 | S8-a Forgot password | 1440 × 900 and 1024 × 768 |
| 24 | S8-b, S8-c Forgot password states | 1440 × 900 |
| 25 | S9-a Deactivate pop-up | 1440 × 900 |
| 26 | S9-b Reactivate pop-up | 1440 × 900 |
| 27 | S9-c Reactivate blocked | 1440 × 900 |
| 28 | S9-d Last admin | 1440 × 900 |
| 29 | S10-a Home, Org Admin | 1440 × 900 |
| 30 | S10-b Home, restricted mode | 1440 × 900 |
| 31 | S11-a Confirm password | 1440 × 900 |
| 32 | S11-b Confirm password, wrong | 1440 × 900 |
| 33 | S12-a Roles list | 1440 × 900 |
| 34 | S12-b Retire blocked | 1440 × 900 |
| 35 | S12-c Retire confirmation | 1440 × 900 |
| 36 | S12-d Role saved | 1440 × 900 |
| 37 | Inactivity warning | 1440 × 900 |

Pop-ups and dialogs are shown over their parent screen, dimmed behind.

---

## 12. Out of scope (do not mock)

- Editing a user after creation
- Bulk user upload
- Clinic onboarding by BEST
- The BEST back-office portal
- Session, client, consent and assessment screens beyond the home-screen examples in S10
