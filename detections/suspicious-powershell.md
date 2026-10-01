# Suspicious PowerShell Detection Runbook

## Objective

Use Windows process-creation telemetry to identify PowerShell executions that deserve analyst review without introducing a custom Wazuh rule.

## Telemetry prerequisite

Windows Process Creation auditing must be enabled. For useful command-line visibility, enable the Windows policy that includes command-line information in process creation events.

The lab already verified Event `4688` generation.

## Analyst query concept

Search Wazuh for Windows process-creation events and inspect:

- `powershell.exe` / `pwsh.exe`
- encoded commands
- hidden/non-interactive execution
- download or execution parameters
- suspicious parent processes
- unusual user accounts
- unusual execution paths

Example Wazuh query starting point:

```text
data.win.system.eventID:4688 AND
(data.win.eventdata.newProcessName:*powershell.exe OR data.win.eventdata.newProcessName:*pwsh.exe)
```

Field names can vary by Windows/Wazuh decoder version, so inspect the actual event JSON before relying on a production query.

## Validation procedure

1. Generate a benign PowerShell process in the lab.
2. Confirm Event `4688` arrives in Wazuh.
3. Verify the process name and command line.
4. Repeat with a clearly suspicious-but-non-destructive test command in the isolated VM.
5. Compare the events and document the distinguishing fields.

## Evidence status

The repository contains evidence proving Event `4688` collection, but it does **not** claim that a dedicated suspicious-PowerShell alert was observed. A dedicated screenshot should be added after the validation procedure is run.
