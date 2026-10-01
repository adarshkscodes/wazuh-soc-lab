# Step 11 — Process / Security Event Investigation

Windows process creation auditing was enabled and Event ID `4688` events were verified on the endpoint.

The investigation workflow is:

1. Identify the process and timestamp.
2. Review the account/security context.
3. Inspect parent process and command line where available.
4. Correlate with preceding/following security events.
5. Determine whether the execution is expected.
6. Preserve the event as evidence when suspicious.

Evidence: `evidence/07-process-creation-event-verification.png`.
