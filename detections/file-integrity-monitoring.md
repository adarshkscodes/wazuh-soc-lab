# File Integrity Monitoring

## Test file

```text
C:\soc-lab\test.txt
```

## Observed alert

Wazuh Syscheck generated rule `550`:

`Integrity checksum changed.`

The captured alert records changes to:

- size
- modification time
- MD5
- SHA-1
- SHA-256

## Example evidence

The detailed alert shows the file changing from `0` to `36` bytes and includes before/after cryptographic hashes.

## MITRE mapping

The captured Wazuh alert provides:

`T1565.001 — Stored Data Manipulation`

## Analyst workflow

1. Confirm path.
2. Confirm timestamp.
3. Compare hashes.
4. Identify user/permissions.
5. Correlate with process creation.
6. Determine whether the change was expected.

## Evidence

- `evidence/05-fim-integrity-alert-details.png`
- `evidence/06-fim-events-overview.png`
