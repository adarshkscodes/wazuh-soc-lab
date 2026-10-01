# SOC Investigation Methodology

## Alert

Record:
- Alert/rule
- Severity
- Endpoint
- Timestamp

## Initial Assessment

- What generated the alert?
- Which Windows event produced the telemetry?
- Is the activity expected?

## Evidence

Collect:
- username
- source IP
- process
- command line
- file path
- hash
- parent process
- related alerts

## Correlation

Build a timeline:

```text
Authentication
    ↓
Process creation
    ↓
File/network activity
    ↓
Wazuh alert
    ↓
Analyst investigation
```

## Conclusion

Use evidence-based language:

```text
Observed:
Confirmed:
Not confirmed:
Assessment:
```

An alert is a signal, not automatically a confirmed incident.
