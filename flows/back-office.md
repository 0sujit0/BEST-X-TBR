# BEST Back Office flows — agreed 2026-10-12 (D-015)

## License lifecycle (Platform Admin)
1. Clinic onboarded and approved (see flows/clinic-onboarding.md, D-018); tenant created
2. Create license: plan, seats, dates, features
3. License active: Org Admins can invite users; Platform Admin can edit seats/features or suspend
4. Org Admins are warned before the end date (configurable, default 30 days)
5. End date reached (checked daily) → license expired: no new sessions; users can still log in and view records; no data deleted
6. Suspend = same effect as expiry, applied manually
7. Platform Admin extends the license to return it to active

## Break-glass access to clinical data
1. BEST staff requests access: reason, scope, expiry
2. BEST security approver approves (first)
3. Clinic Org Admin approves (second)
4. Both must approve; either can decline → request denied and logged
5. No response within a set time → request lapses, treated as denied
6. Access granted → clinic notified; all actions logged
7. Access expires automatically after a configurable maximum → clinic notified
