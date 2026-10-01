# Step 10 — Suspicious PowerShell Detection

## Detection design

The lab uses Windows process-creation auditing as the foundation for PowerShell detection. A SOC analyst can investigate PowerShell executions by looking for process creation events where the executable is PowerShell and then examining command-line arguments.

High-value command-line indicators include:

- `-enc` / `-EncodedCommand`
- `-nop` / `-NoProfile`
- `-w hidden` / `-WindowStyle Hidden`
- `-ExecutionPolicy Bypass`
- `IEX`
- `DownloadString`
- `FromBase64String`
- suspicious external download or execution behavior

## Investigation sequence

```text
4688 process creation
       ↓
Identify powershell.exe / pwsh.exe
       ↓
Capture command line
       ↓
Decode/normalize encoded content when appropriate
       ↓
Check parent process + user + destination
       ↓
Correlate with network/security events
       ↓
Map behavior to ATT&CK if supported by evidence
```

## Evidence integrity

The repository does **not** claim that a suspicious PowerShell alert was captured in this lab. The available screenshots prove process-creation auditing and Wazuh ingestion; this document records the next detection workflow and validation criteria.
