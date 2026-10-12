# Therapist flow — agreed 2026-10-12 (D-012)

1. Select scheduled session from dashboard
2. Consent check (automatic)
   - No consent: in-person session runs with manual notes only, no device data; telehealth cannot start
3. Session type
   - In person: device synced to session
   - Telehealth: video starts; no live soft alerts (v1 §20.10)
4. Live session: indicators show data age
   - Soft alert (in person only) → therapist acknowledges
   - Notes and markers added anytime
5. End session: manual, or automatic when scheduled window closes; unacknowledged alerts expire
6. Session data sent to external AI API → "Summary generating" status
   - Draft returned → review (labeled AI-generated) → edit and confirm
   - Generation failed → retry (no limit) or write manually → confirm
7. Confirmed summary saved to session record; supervisors see confirmed summaries only, never unconfirmed drafts
