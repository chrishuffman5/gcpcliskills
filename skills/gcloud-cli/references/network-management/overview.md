# gcloud network-management — Network Intelligence Center (Connectivity Tests & VPC Flow Logs)

## Overview

`gcloud network-management` manages two Network Intelligence Center (NIC) features for diagnosing and observing Google Cloud networking. **Connectivity Tests** check reachability between network endpoints by analyzing live configuration and performing data-plane traces; **VPC Flow Logs configurations** control which VPC resources (subnets, networks, VPN tunnels, Interconnect attachments) emit flow-log records and how those records are sampled and filtered. Reach for it when you need to troubleshoot why traffic is (or is not) flowing, or to centrally manage flow-log collection at the project or organization level.

## Quick reference — common workflows

### 1. Enable the API and inspect existing resources

```bash
gcloud services enable networkmanagement.googleapis.com

# Existing connectivity tests
gcloud network-management connectivity-tests list --limit=20

# Existing VPC Flow Logs configs (project-level; --location is required)
gcloud network-management vpc-flow-logs-configs list --location=global
```

### 2. Create and run a connectivity test (VM to IP in a peered network)

```bash
gcloud network-management connectivity-tests create my-test \
    --source-instance=projects/my-project/zones/us-west1-a/instances/my-instance \
    --destination-ip-address=10.142.0.2 \
    --destination-network=projects/my-project/global/networks/peering-network \
    --protocol=TCP \
    --destination-port=80

# Inspect the analysis result
gcloud network-management connectivity-tests describe my-test

# Re-run after a config change
gcloud network-management connectivity-tests rerun my-test
```

### 3. Create a VM-to-VM test with return-path tracing

```bash
gcloud network-management connectivity-tests create vm-to-vm-test \
    --source-instance=projects/my-project/zones/us-central1-a/instances/src-vm \
    --destination-instance=projects/my-project/zones/us-central1-b/instances/dst-vm \
    --protocol=TCP \
    --destination-port=443 \
    --round-trip

gcloud network-management connectivity-tests describe vm-to-vm-test
```

### 4. Update and delete a connectivity test

```bash
gcloud network-management connectivity-tests update my-test \
    --description='update dst addr' \
    --destination-ip-address='10.142.0.3'

gcloud network-management connectivity-tests delete my-test
```

### 5. Create a project-level VPC Flow Logs config for a subnet

```bash
gcloud network-management vpc-flow-logs-configs create my-subnet-config \
    --location=global \
    --subnet="projects/my-project/regions/us-central1/subnetworks/my-subnet" \
    --flow-sampling=0.5 \
    --aggregation-interval=interval-5-sec \
    --metadata=include-all-metadata

gcloud network-management vpc-flow-logs-configs describe my-subnet-config \
    --location=global
```

### 6. Pause, re-enable, and inspect effective flow-logs configs

```bash
# Pause log generation without deleting the config
gcloud network-management vpc-flow-logs-configs update my-subnet-config \
    --location=global --state=disabled

# Re-enable and capture all logs
gcloud network-management vpc-flow-logs-configs update my-subnet-config \
    --location=global --state=enabled --flow-sampling=1.0

# Show every config (including inherited org configs) affecting a network
gcloud network-management vpc-flow-logs-configs show-effective-flow-logs-configs \
    --location=global \
    --resource="projects/my-project/global/networks/my-network"

# List org-level configs associated with the current project
gcloud network-management vpc-flow-logs-configs query-org-vpc-flow-logs-configs \
    --location=global
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `network-management connectivity-tests` | [`connectivity-tests.md`](connectivity-tests.md) | 6 | manage Network Management ConnectivityTests |
| `network-management operations` | [`operations.md`](operations.md) | 2 | manage Network Management operations |
| `network-management vpc-flow-logs-configs` | [`vpc-flow-logs-configs.md`](vpc-flow-logs-configs.md) | 7 | manage the VPC Flow Logs configurations |

See [`index.md`](index.md) for a one-line index of all 15 GA commands.

## Common flags & tips

- **Endpoint flags (connectivity-tests create):** a test needs at least one source flag and one destination flag. Sources include `--source-instance`, `--source-ip-address`, `--source-cloud-sql-instance`, `--source-gke-master-cluster`, `--source-cloud-run-revision`, `--source-cloud-function`, `--source-app-engine-version`; destinations include `--destination-instance`, `--destination-ip-address`, `--destination-forwarding-rule`, `--destination-cloud-sql-instance`, `--destination-gke-master-cluster`, `--destination-redis-cluster`, `--destination-redis-instance`. Endpoints are typically full resource URIs (`projects/.../zones/.../instances/...`).
- **`--protocol` / `--destination-port`:** protocol defaults to TCP when omitted; `--destination-port` applies only to TCP/UDP.
- **`--round-trip`:** adds return-path (destination-to-source) traces when the forward packet reaches the destination. `update` supports `--no-round-trip` to turn it off.
- **`--bypass-firewall-checks`:** skips firewall evaluation during analysis (use `--no-bypass-firewall-checks` on `update`).
- **VPC Flow Logs `--location=global` is always required** on every `vpc-flow-logs-configs` command. Add `--organization=<ORG_ID>` (or use a fully qualified `organizations/.../...` resource name) for organization-level configs.
- **Target selector (create/update):** at most one of `--subnet`, `--network`, `--interconnect-attachment`, `--vpn-tunnel`. Omitting all of them with `--organization` creates an org-wide config.
- **Don't set `--flow-sampling=0`:** the value must be in (0, 1]; to stop logging use `--state=disabled` instead.
- **Enum values are lowercased on the CLI:** e.g. `--aggregation-interval=interval-5-sec` (also `interval-30-sec`, `interval-1-min`, `interval-5-min`, `interval-10-min`, `interval-15-min`), `--metadata=include-all-metadata` (or `exclude-all-metadata` / `custom-metadata`), `--state=enabled|disabled`.
- **`--async`** is available on create/update/delete/rerun to return immediately; poll progress with `gcloud network-management operations describe OPERATION` and `... operations list --limit=5`.
- **Filtering / formatting:**
  - `gcloud network-management vpc-flow-logs-configs list --location=global --filter="state:ENABLED"`
  - `gcloud network-management connectivity-tests list --filter="..." --sort-by=NAME --limit=5`
  - `gcloud network-management connectivity-tests describe my-test --format="value(reachabilityDetails.result)"`

## beta / alpha

- `gcloud beta network-management` mirrors all three GA subgroups (`connectivity-tests`, `operations`, `vpc-flow-logs-configs`) and may expose flags before they graduate to GA. There is no documented `gcloud alpha network-management` surface.
- Capabilities such as `--round-trip` (connectivity tests), `--cross-project-metadata` (org-level flow-logs configs), and the `query-org-vpc-flow-logs-configs` / `show-effective-flow-logs-configs` subcommands are available on the GA track documented here.

## Official documentation

- [Network Intelligence Center overview](https://cloud.google.com/network-intelligence-center/docs/overview) — product home; unified console for network visibility across hybrid/multicloud environments.
- [Connectivity Tests concepts](https://cloud.google.com/network-intelligence-center/docs/connectivity-tests/concepts/overview) — how config analysis and live data-plane checks work.
- [Running Connectivity Tests](https://cloud.google.com/network-intelligence-center/docs/connectivity-tests/how-to/running-connectivity-tests) — gcloud how-to covering every endpoint-type flag.
- [Connectivity Tests access control](https://cloud.google.com/network-intelligence-center/docs/connectivity-tests/concepts/access-control) — IAM roles and permissions required to run and view tests.
- [VPC Flow Logs](https://cloud.google.com/vpc/docs/flow-logs) — sampling, aggregation intervals, and metadata-field reference.
- [gcloud network-management CLI reference](https://cloud.google.com/sdk/gcloud/reference/network-management) — full command/flag reference for all subgroups.
- [gcloud beta network-management CLI reference](https://cloud.google.com/sdk/gcloud/reference/beta/network-management) — beta-track command surface.
