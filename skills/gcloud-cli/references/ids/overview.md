# gcloud ids — Cloud IDS (Cloud Intrusion Detection System)

## Overview
Cloud IDS is a managed intrusion-detection service that inspects traffic on a VPC network for
intrusions, malware, spyware, and command-and-control attacks using Palo Alto Networks threat-protection
technologies. It works by creating a Google-managed peered network with mirrored VM instances (an IDS
*endpoint*) that analyzes traffic and emits threat and (optionally) traffic logs. Cloud IDS only detects
and alerts — it does not block traffic — so remediation requires a separate product such as Cloud Next
Generation Firewall. Reach for it when you need PCI/HIPAA-aligned network threat visibility without
running and scaling your own IDS appliances.

## Quick reference — common workflows

### 1. Enable the API and create a basic endpoint
```bash
gcloud services enable ids.googleapis.com

# Create an endpoint on a VPC network, alerting on LOW threats or higher.
# (Private Services Access must already be configured on the VPC.)
gcloud ids endpoints create my-endpoint \
    --network=my-vpc \
    --zone=us-central1-a \
    --severity=LOW \
    --project=my-project
```

### 2. Create an endpoint with a description and threat exceptions
```bash
# Exclude specific Palo Alto threat IDs from alerting.
gcloud ids endpoints create my-endpoint \
    --network=my-vpc \
    --zone=us-central1-a \
    --severity=MEDIUM \
    --description="IDS endpoint for production VPC" \
    --threat-exceptions=1000,2000 \
    --project=my-project
```

### 3. Create an endpoint with traffic logging, and wait for it to become READY
```bash
# --enable-traffic-logs can generate high log volume / Cloud Logging cost.
# --no-async blocks until the endpoint reaches READY (up to --max-wait).
gcloud ids endpoints create my-endpoint \
    --network=my-vpc \
    --zone=us-central1-a \
    --severity=HIGH \
    --enable-traffic-logs \
    --no-async \
    --max-wait=60m \
    --project=my-project
```

### 4. List and inspect endpoints
```bash
# List all endpoints in a project.
gcloud ids endpoints list --project=my-project

# Show only endpoint resource URIs.
gcloud ids endpoints list --project=my-project --uri

# Describe a single endpoint.
gcloud ids endpoints describe my-endpoint \
    --zone=us-central1-a \
    --project=my-project
```

### 5. Update or clear the threat-exception list
```bash
# Replace the excepted threat IDs on an existing endpoint.
gcloud ids endpoints update my-endpoint \
    --zone=us-central1-a \
    --threat-exceptions=1000,2000,3000 \
    --project=my-project

# Clear all threat exceptions (pass an empty list).
gcloud ids endpoints update my-endpoint \
    --zone=us-central1-a \
    --threat-exceptions= \
    --project=my-project
```

### 6. Delete an endpoint
```bash
# Delete by name + zone.
gcloud ids endpoints delete my-endpoint \
    --zone=us-central1-a \
    --project=my-project

# Or delete by fully-qualified resource path (zone/project implied by the path).
gcloud ids endpoints delete \
    projects/my-project/locations/us-central1-a/endpoints/my-endpoint
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `ids endpoints` | [`endpoints.md`](endpoints.md) | 5 | create and manage Cloud IDS Endpoints |

See [`index.md`](index.md) for a one-line index of all 5 commands.

## Common flags & tips
- **Endpoints are zonal.** Every endpoint command identifies its target by name plus `--zone`
  (e.g. `--zone=us-central1-a`), or by a fully-qualified path
  `projects/PROJECT/locations/ZONE/endpoints/NAME` that encodes the project and zone.
- **`--severity` is required on create** and must be one of `INFORMATIONAL`, `LOW`, `MEDIUM`, `HIGH`,
  `CRITICAL`. It sets the *minimum* severity that triggers an alert (lower severities are not reported).
- **`--network` is required on create** and names the VPC network to monitor. The VPC must have
  Private Services Access configured so Cloud IDS can peer its Google-managed network.
- **Async by default.** `create`, `delete`, and `update` return immediately (`--async` is on by default).
  Pass `--no-async` to block until the operation completes, and tune the wait with `--max-wait` (default
  `60m`; see `gcloud topic datetimes` for time formats).
- **`--threat-exceptions`** takes a comma-separated list of threat IDs to suppress; passing an empty
  value (`--threat-exceptions=`) clears the list. It is settable on both `create` and `update`.
- **`--enable-traffic-logs`** (create only) turns on traffic logging in addition to threat logs — useful
  for forensic detail but can substantially increase Cloud Logging cost.
- **Filtering/formatting** on `list`: combine `--filter`, `--sort-by`, `--limit`, and `--uri`, e.g.
  list READY endpoints in a zone:
  ```bash
  gcloud ids endpoints list --project=my-project \
      --filter="state=READY" --sort-by=createTime --format="table(name,network,severity,state)"
  ```

## beta / alpha
- **`gcloud beta ids`** — the full `endpoints` group (create/delete/describe/list/update) is available;
  marked "might change without notice", with no additional flags beyond the GA surface.
- **`gcloud alpha ids`** — includes the `endpoints` group plus an alpha-only `operations` group for
  long-running operations:
  ```bash
  gcloud alpha ids operations list      # List Cloud IDS operations
  gcloud alpha ids operations describe  # Describe an operation
  gcloud alpha ids operations wait      # Wait for an operation to complete
  gcloud alpha ids operations cancel    # Cancel an operation
  ```
  There is no GA or beta equivalent of `operations`.

## Official documentation
- [Cloud IDS documentation home](https://cloud.google.com/intrusion-detection-system/docs) — product docs landing page (concepts, how-to, pricing).
- [Cloud IDS overview](https://cloud.google.com/intrusion-detection-system/docs/overview) — architecture: endpoints, packet mirroring, the Palo Alto threat engine, and compliance (PCI 11.4, HIPAA).
- [Cloud IDS logging](https://cloud.google.com/intrusion-detection-system/docs/logging) — threat-log and traffic-log structure, fields, and 30-day retention.
- [IAM roles for Cloud IDS](https://cloud.google.com/iam/docs/roles-permissions/ids) — `roles/ids.admin`, `roles/ids.editor`, `roles/ids.viewer`.
- [gcloud ids reference](https://cloud.google.com/sdk/gcloud/reference/ids) — GA command reference for the `endpoints` group.
