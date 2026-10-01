# Step 7 — Brute-Force Detection Concept

## Objective

Define how repeated Windows authentication failures could be investigated as a possible brute-force pattern.

## Concept

A single Event ID 4625 indicates a failed logon. A brute-force investigation requires **aggregation and context**, not one isolated event.

Useful correlation fields include:

- source IP / workstation
- target account
- timestamp
- logon type
- number of failures
- successful logon following failures
- affected hosts

## Analyst logic

```text
4625 failures
    ↓
Group by source + account
    ↓
Measure failures over time
    ↓
Check for successful 4624 events
    ↓
Check account / host context
    ↓
Decide: benign / suspicious / escalate
```

The project does not spend additional time forcing an automated brute-force alert. The detection concept and investigation methodology are documented because the primary objective is demonstrating SOC reasoning.
