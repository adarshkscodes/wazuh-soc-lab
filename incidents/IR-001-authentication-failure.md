# IR-001 — Windows Authentication Failure

## Classification

**Type:** Authentication monitoring / failed logon

**Evidence:** Windows Security Event `4625` / Wazuh rule `60122`

**Environment:** `WIN11-SOC-AGENT`

## Observed

The Wazuh event contains Windows Security telemetry for an unsuccessful logon. The displayed rule description is:

`Logon Failure - Unknown user or bad password`

The event details include authentication context such as the account, logon type, source address and authentication package.

## Investigation

1. Confirm the event ID and Wazuh rule.
2. Identify the target account.
3. Review source address and workstation information.
4. Review logon type and authentication package.
5. Check whether failures repeat.
6. Correlate with successful logons, process creation and endpoint activity.

## Assessment

A failed authentication event is a **detection signal**, not by itself proof of credential attack or compromise. In this controlled lab, the event was intentionally generated for validation.

## Evidence

- `evidence/03-authentication-failure-events.png`
- `evidence/04-authentication-failure-details.png`

## MITRE context

The Wazuh event displayed a MITRE mapping. The mapping is recorded as telemetry supplied by the Wazuh rule; the analyst should validate the technique against the actual behavior and surrounding evidence before treating it as an incident classification.
