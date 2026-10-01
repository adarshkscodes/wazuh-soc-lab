# Step 4 — Alert Investigation

The analyst opened the individual 4625 alert and reviewed the structured event fields rather than relying only on the alert title.

Investigation fields included:

- event ID
- target account
- source/workstation information
- logon type
- authentication package
- failure status/substatus
- process information
- timestamp

This establishes a repeatable triage method for Windows authentication alerts.

Evidence: `evidence/04-authentication-failure-details.png`.
