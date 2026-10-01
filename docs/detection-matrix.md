# Detection Matrix

| Use case | Source | Observable | Wazuh output | Status |
|---|---|---|---|---|
| Failed authentication | Windows Security | Event 4625 | Rule 60122 | Verified |
| FIM modification | Syscheck | File change + hash delta | Rule 550 | Verified |
| File creation | Syscheck | New file | Rule 554 | Verified |
| Process creation | Windows Security | Event 4688 | Windows event telemetry | Verified |
| Suspicious PowerShell | Windows Security | 4688 + PowerShell command line | Analyst runbook | Runbook ready; live alert evidence pending |

The matrix distinguishes observed detections from planned analyst coverage.
