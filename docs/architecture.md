# Lab Architecture

```text
                    +--------------------------+
                    |       Kali Linux         |
                    |     SOC Analyst VM       |
                    +------------+-------------+
                                 |
                                 | HTTPS
                                 v
                    +--------------------------+
                    |    Wazuh Dashboard       |
                    |      Ubuntu 24.04        |
                    +------------+-------------+
                                 |
                    +------------v-------------+
                    |      Wazuh Manager       |
                    |     Detection Engine     |
                    +------------+-------------+
                                 |
                    +------------v-------------+
                    |      Wazuh Indexer       |
                    +------------^-------------+
                                 |
                          Wazuh Agent
                                 |
                    +------------+-------------+
                    |       Windows 11         |
                    |     WIN11-SOC-AGENT      |
                    |  4625 / 4688 / FIM       |
                    +--------------------------+
```

Data flow:

```text
Windows activity
  -> Windows Event Log / Syscheck
  -> Wazuh Agent
  -> Wazuh Manager
  -> Decoders + Rules
  -> Alert
  -> Indexer
  -> Dashboard
  -> SOC investigation
```
