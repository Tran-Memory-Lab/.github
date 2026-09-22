# Security and data-protection policy

## Reporting

Report a vulnerability, an exposed secret, or participant data found in any Tran Memory Lab
repository **privately** to a lab administrator (an owner of the Tran-Memory-Lab organization). Do not open a
public issue, and do not copy the exposed material into the report.

## If participant data or a secret was committed

1. Tell a lab administrator immediately.
2. Do not try to fix it with a new commit; deleting a file does not remove it from Git history.
3. An administrator rotates any secret and decides whether history must be rewritten and who must
   be notified under the IRB protocol.

## Never commit

- credentials, tokens, API keys, or `.env` files;
- raw participant data, raw gaze logs, raw exports, participant identifiers;
- uncurated video or audio.

Only synthetic fixtures, de-identified toy datasets, schemas, and test manifests belong in Git.
