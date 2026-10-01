# Incident Investigation Workflow

This lab uses a lightweight SOC workflow that can be applied to Windows endpoint alerts.

```text
Alert
  ↓
Validate telemetry
  ↓
Identify user / host / source
  ↓
Build timeline
  ↓
Correlate authentication + process + file activity
  ↓
Determine expected vs suspicious
  ↓
Document evidence
  ↓
Contain / escalate when justified
  ↓
Close with analyst conclusion
```

## Analyst record

For each alert, record:

- Alert/rule ID and severity
- Endpoint and agent ID
- Timestamp and timezone
- User/account
- Source IP or source host when available
- Windows event ID
- Process and command line when available
- File path and hashes when relevant
- Related events before and after the alert
- Expected/authorized change context
- Analyst conclusion
- Recommended response

## Evidence standard

Use three labels:

**Observed** — directly visible in Wazuh/Windows telemetry.

**Confirmed** — supported by multiple pieces of evidence or controlled reproduction.

**Not confirmed** — plausible interpretation that requires additional telemetry.

This distinction is used throughout the project.
