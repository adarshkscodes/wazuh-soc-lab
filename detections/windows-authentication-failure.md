# Windows Authentication Failure Detection

## Event

`4625 — An account failed to log on`

## Wazuh observation

The captured lab event was processed as Wazuh rule `60122`:

`Logon Failure - Unknown user or bad password`

## Investigation fields

Review:

- target account
- source address
- workstation name
- logon type
- authentication package
- status/substatus
- process information
- event timestamp

## Analyst approach

A single failed logon can be normal. Investigate repetition, unusual sources, account targeting, timing and correlation with successful authentication or endpoint activity before escalating.

## Evidence

- `evidence/03-authentication-failure-events.png`
- `evidence/04-authentication-failure-details.png`
