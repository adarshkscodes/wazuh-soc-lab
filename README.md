# Wazuh SOC Detection & Investigation Lab

> A hands-on Security Operations Center portfolio project demonstrating Windows telemetry collection, Wazuh detection, alert investigation, MITRE ATT&CK mapping, File Integrity Monitoring, process monitoring, and incident documentation.

![Wazuh](https://img.shields.io/badge/Wazuh-4.x-blue)
![Windows](https://img.shields.io/badge/Windows-11-informational)
![SOC](https://img.shields.io/badge/Focus-SOC%20%2F%20SIEM-success)
![MITRE ATT%26CK](https://img.shields.io/badge/MITRE%20ATT%26CK-mapped-orange)

## Project objective

Build and document an end-to-end SOC workflow:

**Generate security event → collect telemetry → detect → investigate → map to MITRE ATT&CK → document incident → preserve evidence.**

The project intentionally skips implementation of custom Wazuh rules and brute-force automation after validating the concepts. The portfolio focuses on demonstrating analyst workflow rather than artificially inflating the number of detections.

## Lab architecture

```text
                 ┌──────────────────────────┐
                 │        Kali Linux        │
                 │   SOC analyst / testing  │
                 └────────────┬─────────────┘
                              │
                              │ HTTP / browser
                              ▼
┌─────────────────────┐   Wazuh telemetry   ┌──────────────────────┐
│ Windows 11 ARM64    │ ──────────────────► │ Ubuntu 24.04 ARM64   │
│ WIN11-SOC-AGENT     │                     │ SOC-WAZUH             │
│ Security Events     │                     │ Wazuh manager/indexer │
│ FIM / process logs  │                     │ dashboard             │
└─────────────────────┘                     └──────────────────────┘
```

## Lab components

| Component | Role | Validation |
|---|---|---|
| Windows 11 | Endpoint / Wazuh agent | Agent, Security events, FIM |
| Ubuntu 24.04 | Wazuh server | Manager/indexing/dashboard workflow |
| Kali Linux | Analyst workstation | Investigation and testing |
| Wazuh | SIEM/XDR platform | Detection, investigation, ATT&CK context |

## Exact project roadmap

| # | Step | Status | Evidence / artifact |
|---:|---|---|---|
| 1 | Windows security event generation | ✅ Complete | Security event evidence |
| 2 | Wazuh agent → manager ingestion | ✅ Complete | Wazuh event results |
| 3 | 4625 failed-login detection | ✅ Complete | Rule 60122 |
| 4 | Alert investigation | ✅ Complete | Detailed 4625 document |
| 5 | MITRE ATT&CK mapping | ✅ Complete | T1531 mapping |
| 6 | Custom Wazuh rule concept | ✅ Documented | `docs/06-custom-rule-concept.md` |
| 7 | Brute-force detection concept | ✅ Documented | `docs/07-bruteforce-concept.md` |
| 8 | FIM configuration | ✅ Complete | FIM configuration/evidence |
| 9 | FIM investigation | ✅ Complete | Rule 550 / checksum change |
| 10 | Suspicious PowerShell detection | 🟡 Detection design documented | `detections/suspicious-powershell.md` |
| 11 | Process/security event investigation | ✅ Complete | Event 4688 verification |
| 12 | MITRE ATT&CK investigation workflow | ✅ Complete | `docs/12-mitre-investigation-workflow.md` |
| 13 | SOC incident case/report | ✅ Complete | `incidents/` |
| 14 | GitHub documentation | ✅ Complete | This repository |
| 15 | Final portfolio project | 🟢 Portfolio-ready | Complete project package |

> **Evidence integrity note:** only observations supported by the captured lab screenshots are presented as executed detections. PowerShell is documented as a detection design/validation procedure rather than claiming an alert that was not captured.

## Key detections demonstrated

### Windows authentication failure — Event ID 4625

The Windows endpoint generated failed authentication telemetry and Wazuh ingested it. The captured alert includes:

- Rule ID: `60122`
- Description: `Logon Failure - Unknown user or bad password`
- Windows Event ID: `4625`
- Agent: `WIN11-SOC-AGENT`
- MITRE ATT&CK: `T1531 – Account Access Removal` as mapped by the observed Wazuh rule

See [`detections/windows-authentication-failure.md`](detections/windows-authentication-failure.md) and [`incidents/IR-001-authentication-failure.md`](incidents/IR-001-authentication-failure.md).

### File Integrity Monitoring

A controlled test file was modified on the Windows endpoint. Wazuh generated an integrity-change alert showing changes to size, modification time, MD5, SHA-1 and SHA-256 values.

Observed alert:

- Rule ID: `550`
- Level: `7`
- Description: `Integrity checksum changed.`
- Path: `C:\soc-lab\test.txt`
- Mode: `realtime`
- MITRE ATT&CK: `T1565.001 – Stored Data Manipulation`

See [`detections/file-integrity-monitoring.md`](detections/file-integrity-monitoring.md) and [`incidents/IR-002-fim-file-modification.md`](incidents/IR-002-fim-file-modification.md).

### Process creation

Windows process creation auditing was enabled and Event ID `4688` events were verified on the endpoint. This provides the foundation for command-line and PowerShell investigation.

See [`detections/process-creation.md`](detections/process-creation.md).

## Investigation methodology

Every alert is handled using the same analyst workflow:

1. **Validate** the alert and identify the affected host.
2. **Scope** the event using timestamp, user, source, destination and process fields.
3. **Correlate** related Windows/Wazuh telemetry.
4. **Determine** whether the activity is expected, suspicious, or malicious.
5. **Map** relevant behavior to MITRE ATT&CK.
6. **Document** evidence, analysis, impact and recommended response.
7. **Close or escalate** with a defensible rationale.

See [`docs/investigation-methodology.md`](docs/investigation-methodology.md).

## Evidence gallery

All screenshots are stored locally in [`evidence/`](evidence/).

| Evidence | Demonstrates |
|---|---|
| `01-agent-status.png` | Wazuh endpoint/agent state |
| `02-agent-security-dashboard.png` | Endpoint telemetry and ATT&CK/security dashboard |
| `03-authentication-failure-events.png` | Failed-login events in Wazuh |
| `04-authentication-failure-details.png` | Detailed Event 4625 investigation |
| `05-fim-integrity-alert-details.png` | Detailed Rule 550 FIM alert |
| `06-fim-events-overview.png` | FIM event stream |
| `07-process-creation-event-verification.png` | Event 4688 process-creation verification |

## Repository structure

```text
wazuh-soc-lab/
├── README.md
├── evidence/
├── detections/
├── incidents/
├── docs/
├── .gitignore
└── LICENSE
```

## Portfolio value

This project demonstrates practical SOC skills rather than only tool installation:

- Windows security telemetry
- SIEM ingestion and alert triage
- Wazuh investigation
- File Integrity Monitoring
- Authentication failure analysis
- Process creation monitoring
- MITRE ATT&CK contextualization
- Evidence preservation
- Incident documentation
- Detection engineering concepts

## Important lab note

The lab uses controlled activity on a private virtualized environment. No production systems or third-party accounts are targeted.
