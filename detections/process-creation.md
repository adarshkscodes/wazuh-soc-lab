# Windows Process Creation Monitoring

## Objective

Collect Windows process-creation telemetry so the analyst can correlate executable activity with authentication and file events.

## Configuration validated in the lab

```powershell
auditpol /set /subcategory:"Process Creation" /success:enable
auditpol /get /subcategory:"Process Creation"
```

The Windows Security log was queried for Event `4688`:

```powershell
Get-WinEvent -FilterHashtable @{
    LogName='Security'
    Id=4688
    StartTime=(Get-Date).AddMinutes(-5)
} | Select-Object -First 10 TimeCreated, Id, Message
```

## Analyst fields

Review:

- new process name
- command line, when configured
- parent/creator process
- user
- process ID
- timestamp

## Evidence

`evidence/07-process-creation-event-verification.png`

The evidence demonstrates that Event `4688` was generated on the Windows endpoint after enabling Process Creation auditing.
