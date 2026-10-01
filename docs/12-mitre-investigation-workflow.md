# Step 12 — MITRE ATT&CK Investigation Workflow

MITRE ATT&CK is used as an investigation context layer, not as a replacement for evidence.

## Workflow

1. Identify the observable behavior.
2. Confirm the event fields and affected asset.
3. Identify the ATT&CK technique/sub-technique represented by the observed behavior or Wazuh mapping.
4. Review related telemetry for corroboration.
5. Document why the mapping is relevant.
6. Avoid treating a technique mapping alone as proof of compromise.

## Project examples

| Investigation | Observed behavior | ATT&CK context |
|---|---|---|
| Authentication failure | Windows Event 4625 | Wazuh observed mapping: T1531 |
| FIM modification | File contents/hash changed | T1565.001 Stored Data Manipulation |
| Process creation | Windows Event 4688 | Foundation for execution/process analysis |

The ATT&CK mapping is always interpreted together with the underlying telemetry.
