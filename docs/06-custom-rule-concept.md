# Step 6 — Custom Wazuh Rule Concept

## Objective

Understand how a SOC analyst would convert a useful recurring event pattern into a custom Wazuh rule without claiming that a custom rule was required for this lab.

## Detection-engineering workflow

```text
Raw Windows event
      ↓
Decoder / parsed fields
      ↓
Existing Wazuh rule
      ↓
Identify recurring high-value pattern
      ↓
Define rule conditions
      ↓
Set severity and MITRE metadata
      ↓
Test safely with wazuh-logtest
      ↓
Deploy only after validation
```

## Example concept

For repeated authentication failures, a custom rule could correlate multiple Event ID 4625 events from the same source or against the same account within a defined interval.

The actual project intentionally **does not deploy a custom rule**. The built-in Wazuh detection was sufficient to demonstrate the analyst workflow and avoids adding unvalidated configuration merely for portfolio appearance.

## Interview takeaway

A SOC analyst should be able to explain the difference between:

- a vendor/built-in detection,
- a local custom rule,
- event correlation,
- threshold-based detection, and
- alert enrichment with MITRE ATT&CK metadata.
