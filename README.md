# OCI Ampere VM Provisioner

Automated 24/7 background provisioner for Oracle Cloud Infrastructure (OCI) Ampere A1 (ARM) Always Free instances in contested regions (like Hyderabad `ap-hyderabad-1`).

## How It Works
- Runs every 30 minutes via GitHub Actions cron.
- Executes an internal 25-minute polite auto-retry loop (2-minute intervals) calling OCI Resource Manager to apply the stack.
- Prevents 429 TooManyRequests rate limits.
- Stops and exits immediately when the VM is successfully created (`SUCCEEDED`).

## Required GitHub Repository Secrets
Under **Settings > Secrets and variables > Actions**:
- `OCI_USER_OCID`
- `OCI_TENANCY_OCID`
- `OCI_FINGERPRINT`
- `OCI_REGION` (e.g. `ap-hyderabad-1`)
- `OCI_KEY_FILE` (Private `.pem` key content)
- `OCI_STACK_ID` (Resource Manager Stack OCID)
