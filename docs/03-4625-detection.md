# Step 3 — Event ID 4625 Failed-Login Detection

The lab produced Windows Event ID `4625`, representing an unsuccessful logon attempt.

Observed Wazuh alert:

- Rule: `60122`
- Description: `Logon Failure - Unknown user or bad password`
- Level: `5`
- Decoder: `windows_eventchannel`
- Agent: `WIN11-SOC-AGENT`

Evidence: `evidence/03-authentication-failure-events.png` and `evidence/04-authentication-failure-details.png`.
