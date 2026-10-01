# Step 1 — Windows Security Event Generation

Windows security auditing was enabled on the Windows 11 SOC endpoint. The lab generated controlled security activity and verified that Windows produced Security log events.

The project captured Event ID `4625` failed-logon telemetry and verified Event ID `4688` process-creation telemetry.

Evidence: `evidence/03-authentication-failure-events.png` and `evidence/07-process-creation-event-verification.png`.
