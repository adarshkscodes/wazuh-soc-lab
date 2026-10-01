# Project Status — 15-Step SOC Roadmap

| # | Step | Status | Evidence |
|---:|---|---|---|
| 1 | Windows security event generation | ✅ Complete | Security event screenshots |
| 2 | Wazuh agent → manager ingestion | ✅ Complete | Wazuh agent/event evidence |
| 3 | 4625 failed-login detection | ✅ Complete | Rule 60122 |
| 4 | Alert investigation | ✅ Complete | Detailed 4625 event |
| 5 | MITRE ATT&CK mapping | ✅ Complete | Wazuh ATT&CK metadata |
| 6 | Custom Wazuh rule concept | ✅ Documented | Detection engineering note |
| 7 | Brute-force detection concept | ✅ Documented | Correlation workflow |
| 8 | FIM configuration | ✅ Complete | Rule 550 evidence |
| 9 | FIM investigation | ✅ Complete | Before/after hashes and metadata |
| 10 | Suspicious PowerShell detection | 🟡 Design documented | Validation workflow; no fabricated alert |
| 11 | Process/security event investigation | ✅ Complete | Event 4688 verification |
| 12 | MITRE ATT&CK investigation workflow | ✅ Complete | Investigation methodology |
| 13 | SOC incident case/report | ✅ Complete | IR-001 / IR-002 |
| 14 | GitHub documentation | ✅ Complete | Repository structure |
| 15 | Final portfolio project | 🟢 Ready | README + docs + evidence |

### Evidence policy

Only events supported by captured screenshots are presented as executed lab results. Detection concepts and validation procedures are clearly marked when no captured alert exists.
