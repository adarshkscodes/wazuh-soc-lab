# Lab Setup

## Topology

```text
                 SOC Analyst
                  Kali Linux
                      |
                      | investigation
                      v
             +------------------+
             |   Ubuntu 24.04   |
             |  Wazuh Platform  |
             | Manager/Indexer/ |
             |    Dashboard     |
             +------------------+
                      ^
                      | telemetry
                      |
             +------------------+
             |    Windows 11    |
             | WIN11-SOC-AGENT  |
             | Wazuh Agent 001  |
             +------------------+
```

## Lab scope

- Windows 11 ARM64 endpoint
- Ubuntu 24.04 ARM64 Wazuh server stack
- Kali Linux analyst workstation
- Private virtual-network communication

## Important note

This repository documents the lab and its evidence. Credentials, agent keys and other secrets are intentionally excluded.
