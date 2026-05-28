# gcloud anthos — Anthos / GKE Enterprise

## Overview
`gcloud anthos` manages **GKE Enterprise** (formerly Anthos) platform building blocks from the command line: it provisions and operates **Anthos Config Controller** instances (a hosted bundle of Config Connector, Config Sync, and Policy Controller for declarative, GitOps-driven management of Google Cloud resources) and handles client-side **authentication** to attached/multi-cloud clusters. Reach for it when you need a managed KRM API host for fleet/infrastructure config, or when you need to generate a login config and authenticate `kubectl` against an Anthos cluster. Most day-to-day fleet, membership, and policy operations live under sibling groups (`gcloud container fleet`, `gcloud container hub`), while `gcloud anthos` itself focuses on Config Controller lifecycle and Anthos client login.

## Quick reference — common workflows

### 1. Enable APIs and create a Config Controller instance
```bash
# Enable the required APIs (Config Controller host + GKE + resource/usage mgmt)
gcloud services enable krmapihosting.googleapis.com \
    container.googleapis.com \
    cloudresourcemanager.googleapis.com \
    serviceusage.googleapis.com

# Create a Standard-mode instance
gcloud anthos config controller create acc-default \
    --location=us-central1

# Or create a fully-managed (Autopilot) instance
gcloud anthos config controller create acc-default \
    --location=us-central1 \
    --full-management
```

### 2. Get credentials and inspect an instance
```bash
# Point kubectl at the instance (writes kubeconfig credentials)
gcloud anthos config controller get-credentials acc-default \
    --location=us-central1

# Show instance details
gcloud anthos config controller describe acc-default \
    --location=us-central1

# List instances across all regions (or scope with --location)
gcloud anthos config controller list
gcloud anthos config controller list --location=us-central1 --full-name
```

### 3. Retrieve the Config Connector identity and grant it access
```bash
# Print the default Config Connector Google Service Account
gcloud anthos config controller get-config-connector-identity acc-default \
    --location=us-central1

# Grant that service account project-level access so it can manage resources
gcloud projects add-iam-policy-binding PROJECT_ID \
    --member="serviceAccount:SA_EMAIL" \
    --role=roles/editor
```

### 4. Monitor Config Controller operations
```bash
# List long-running operations in a region (or all regions)
gcloud anthos config operations list --location=us-central1

# Describe one operation
gcloud anthos config operations describe OPERATION_ID \
    --location=us-central1
```

### 5. Generate a login config and authenticate a cluster
```bash
# Generate the login config from an existing kubeconfig
gcloud anthos create-login-config \
    --kubeconfig=my-kube-config.yaml \
    --output=kubectl-anthos-config.yaml

# Authenticate against a cluster using the login config
gcloud anthos auth login \
    --cluster=my-cluster \
    --login-config=kubectl-anthos-config.yaml

# Print the kubectl commands without running them (dry run)
gcloud anthos auth login --cluster=my-cluster \
    --login-config=kubectl-anthos-config.yaml --dry-run

# Server-side login (no login config file)
gcloud anthos auth login --cluster=my-cluster \
    --server=https://my-api-server-url
```

### 6. Delete a Config Controller instance
```bash
# Async delete (returns immediately)
gcloud anthos config controller delete acc-default \
    --location=us-central1 --async

# Synchronous delete (waits for completion)
gcloud anthos config controller delete acc-default \
    --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `anthos auth` | [`auth.md`](auth.md) | 1 | Authenticate clusters using the Anthos client (`auth login`) |
| `anthos config` | [`config.md`](config.md) | 8 | Config Controller instance lifecycle (`config controller`) and operations (`config operations`) |
| _(top-level)_ | [`_commands.md`](_commands.md) | 1 | `create-login-config` — generate a login configuration file |

See [`index.md`](index.md) for a one-line index of all 10 GA commands.

## Common flags & tips
- **`--location` is required for nearly everything under `config`.** Supported regions are limited: `us-central1`, `us-east1`, `us-east4`, `us-east5`, `us-west2`, `northamerica-northeast1/2`, `europe-north1`, `europe-west1/3/6`, `australia-southeast1/2`, `asia-northeast1/2`, and `asia-southeast1`.
- **Standard vs. fully managed:** `--full-management` on `config controller create` enables the fully-managed (Autopilot) cluster type; omit it for a Standard-mode instance.
- **Networking on create:** customize the backing GKE cluster with `--network`, `--subnet`, `--cluster-ipv4-cidr-block`, `--services-ipv4-cidr-block`, `--master-ipv4-cidr-block`, `--man-blocks` (master authorized networks; `--man-block` is deprecated), and `--use-private-endpoint`.
- **Async vs. sync:** `--async` on `create`/`delete` returns immediately; without it the CLI waits for the operation and you can track progress with `config operations list/describe`.
- **`list` formatting:** `config controller list` and `config operations list` accept the standard `--filter`, `--limit`, `--page-size`, and `--sort-by` flags, e.g.:
  ```bash
  gcloud anthos config controller list --location=us-central1 \
      --filter="name:acc" --format="table(name, state)"
  gcloud anthos config operations list --location=us-central1 \
      --filter="done=false" --sort-by=~startTime
  ```
- **`--full-name`** on `config controller list` prints the fully qualified instance resource name.
- **Auth login options:** add `--kubeconfig` to target a non-default kubeconfig, `--user` to distinguish multiple accounts in one file, `--set-preferred-auth` to force-update the preferred auth method, and `--no-browser` / `--remote-bootstrap` for headless/second-device login flows. `--login-config` accepts a file path or a URL (use `--login-config-cert` to trust a CA for HTTPS URLs).

## beta / alpha
Capabilities not present in GA `gcloud anthos`:

| Command | Track | Notes |
|---------|-------|-------|
| `gcloud beta anthos apply LOCAL_DIR` | beta + alpha | Apply Anthos infrastructure configuration changes from a local directory |
| `gcloud beta anthos export CLUSTER` | beta + alpha | Export an Anthos cluster's current configuration to a directory |
| `gcloud alpha anthos config controller update` | alpha only | Update a Config Controller instance (no GA/beta equivalent) |

GA `gcloud anthos` provides only `create-login-config`, `auth login`, and the `config controller` / `config operations` subgroups.

## Official documentation
- **GKE Enterprise (Anthos) docs home:** https://cloud.google.com/kubernetes-engine/enterprise/docs — product overview, setup, and how-to guides for the GKE Enterprise platform.
- **Config Controller overview:** https://cloud.google.com/anthos-config-management/docs/concepts/config-controller-overview — hosted Config Connector + Config Sync + Policy Controller.
- **Config Controller setup:** https://docs.cloud.google.com/kubernetes-engine/enterprise/config-controller/docs/setup — APIs to enable, instance creation, credential retrieval.
- **Config Controller IAM:** https://docs.cloud.google.com/kubernetes-engine/enterprise/config-controller/docs/iam — least-privilege roles and Config Connector service account binding.
- **Policy Controller overview:** https://docs.cloud.google.com/kubernetes-engine/enterprise/policy-controller/docs/overview — constraint-based guardrails built on OPA Gatekeeper.
- **Config Connector overview:** https://cloud.google.com/config-connector/docs/overview — Kubernetes CRDs for managing Google Cloud resources declaratively.
- **gcloud anthos CLI reference:** https://cloud.google.com/sdk/gcloud/reference/anthos — all subcommands and flags.

See [`sources.md`](sources.md) for the full citation record.
