# IR-002 — File Integrity Change

## Classification

**Type:** File Integrity Monitoring

**Evidence:** Wazuh Syscheck rule `550`

**Endpoint:** `WIN11-SOC-AGENT`

**Path:** `C:\soc-lab\test.txt`

## Observed

Wazuh reported:

`Integrity checksum changed.`

The alert recorded changes to file size, modification time, MD5, SHA-1 and SHA-256 values. The evidence shows the file changing from size `0` to `36` bytes and provides before/after hash values.

## Investigation

1. Confirm the affected path.
2. Compare before/after size and timestamps.
3. Compare cryptographic hashes.
4. Identify the user and permissions associated with the file.
5. Correlate the timestamp with process creation and authentication events.
6. Determine whether the change was an authorized lab action.

## Assessment

The file modification was intentionally performed as a controlled FIM test. The alert demonstrates that Wazuh can detect integrity changes and preserve useful forensic context.

## MITRE ATT&CK

The captured Wazuh alert maps the behavior to:

`T1565.001 — Stored Data Manipulation`

The mapping is documented as the rule-provided classification.

## Evidence

- `evidence/05-fim-integrity-alert-details.png`
- `evidence/06-fim-events-overview.png`
