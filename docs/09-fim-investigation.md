# Step 9 — FIM Investigation

The analyst investigated the Rule 550 alert and compared before/after values.

Observed evidence includes:

- file path: `C:\soc-lab\test.txt`
- size before: `0`
- size after: `36`
- MD5 before/after
- SHA-1 before/after
- SHA-256 before/after
- modification time before/after
- Windows owner/permission context

This demonstrates that FIM alerts can be investigated at the file-change level instead of treated as simple notifications.

Evidence: `evidence/05-fim-integrity-alert-details.png` and `evidence/06-fim-events-overview.png`.
