# Step 8 — File Integrity Monitoring Configuration

FIM was configured on the Windows endpoint in realtime mode for the controlled lab file:

`C:\soc-lab\test.txt`

The test demonstrated that Wazuh can detect changes to protected file attributes and cryptographic hashes.

The captured alert reports:

- event: `modified`
- mode: `realtime`
- changed attributes: `size, mtime, md5, sha1, sha256`
- rule: `550`
- level: `7`

Evidence: `evidence/05-fim-integrity-alert-details.png`.
