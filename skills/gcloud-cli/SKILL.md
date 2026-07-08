---
name: gcloud-cli
description: >-
  gcloud CLI reference: 128 GCP services, all GA commands with full flags, plus the
  standalone bq CLI. Use for any Google Cloud / GCP command-line task — managing
  resources, debugging gcloud commands, auth/config/scripting — or whenever a GCP
  product is named (GKE, Cloud Run, BigQuery, Cloud SQL, Pub/Sub...), even without
  'gcloud'.
---

# gcloud CLI Reference

Complete `gcloud` command reference covering **128 Google Cloud services** and **5,261 GA
commands**, plus the standalone **`bq`** BigQuery CLI. Each service is a self-contained
sub-skill in its own folder, named after its `gcloud` command group. This top-level skill gives
you the CLI conventions plus a routing protocol — read only the one service you need, not the
whole catalog.

## Routing — find the right service

Each service lives at `<gcloud-group>/SKILL.md`, where `<gcloud-group>` is the gcloud
command-group name. **If you already know the group, read its `SKILL.md` directly — do not
load the full index.**

- `gcloud compute …`   → [`compute/SKILL.md`](compute/SKILL.md)
- `gcloud run …`       → [`run/SKILL.md`](run/SKILL.md)
- `gcloud container …` → [`container/SKILL.md`](container/SKILL.md)
- `gcloud storage …`   → [`storage/SKILL.md`](storage/SKILL.md)
- `gcloud sql …`       → [`sql/SKILL.md`](sql/SKILL.md)
- `gcloud iam …`       → [`iam/SKILL.md`](iam/SKILL.md)
- `gcloud pubsub …`    → [`pubsub/SKILL.md`](pubsub/SKILL.md)

Each service's `SKILL.md` has an overview, common workflows, a command-group map,
service-specific tips, and beta/alpha notes. The command-group files alongside it (e.g.
`compute/instances.md`, `storage/buckets.md`) hold the full per-command synopses, flags, value
types, choices, defaults, and examples; `index.md` is the one-line command list and
`sources.md` the official documentation URLs.

**If you don't know the gcloud group name** (e.g. you only know the marketing name), read
[`service-index.md`](service-index.md) — the full table of all services with scope and
official-doc links.

### Non-obvious name → folder mappings

The folder is the gcloud command-group name, which often differs from the product's marketing
name:

| Product (marketing) | Folder / `gcloud` group |
|---|---|
| GKE / Kubernetes Engine | `container` |
| Cloud Storage (GCS, `gs://`) | `storage` (legacy `gsutil` → same folder) |
| BigQuery | `bq-cli` (standalone `bq` tool — the day-to-day CLI); `bq` is *only* Migration Service |
| Vertex AI | `ai` (legacy AI Platform → `ai-platform`; Workbench → `workbench`, `notebooks`) |
| Vertex AI Agent Retrieval / Vector Search 2.0 | `vector-search` (classic Vector Search indexes → `ai`) |
| Memorystore | `redis`, `memcache`, or `memorystore` (Valkey) |
| App Engine | `app` |
| Cloud Build | `builds` |
| Artifact Registry | `artifacts` |
| Cloud Functions (Cloud Run functions) | `functions` |
| Media CDN | `edge-cache` |
| Managed Microsoft AD | `active-directory` |
| Cloud Composer (managed Airflow) | `composer` |
| Enable/disable APIs (Service Usage) | `services` |
| Secret Manager | `secrets` |
| Security Command Center | `scc` |
| Certificate Authority Service | `privateca` (Google-trusted public certs → `publicca`) |
| Managed Service for Apache Kafka | `managed-kafka` |
| Personalized Service Health | `service-health` |
| Projects / folders / organizations | `projects`, `resource-manager`, `organizations` |
| BigLake / Lakehouse Iceberg REST catalog | `biglake` |

For anything not listed, the folder matches the `gcloud <group>` name. See
[`service-index.md`](service-index.md) for the complete list.

**REQUIRED:** Read the target service's `SKILL.md` before constructing commands for it.

> **Release tracks:** this reference covers **GA** commands. Many services also expose
> additional commands under `gcloud beta <service>` and `gcloud alpha <service>`; each service
> SKILL.md notes where important capabilities are beta/alpha-only.

## Top-level CLI commands (not services)

These manage the CLI itself rather than cloud resources:

- `gcloud init` — interactive first-time setup (auth + default project/region).
- `gcloud auth` — manage credentials. See [`auth/SKILL.md`](auth/SKILL.md).
- `gcloud config` — view/set CLI properties (project, region, zone, account). See [`config/SKILL.md`](config/SKILL.md).
- `gcloud components` — install/update/remove CLI components. See [`components/SKILL.md`](components/SKILL.md).
- `gcloud info` — show CLI environment/diagnostics (`gcloud info --run-diagnostics` checks network/auth issues).  `gcloud version` — show component versions.

## Companion CLIs bundled with the Google Cloud SDK

Not everything on GCP is a `gcloud` command. These separate tools install alongside gcloud
(via `gcloud components install <id>` where noted):

- **`bq`** — the day-to-day **BigQuery** CLI (`bq query`, `bq load`, `bq mk`, `bq extract`, …),
  invoked as plain `bq ...`. This is NOT `gcloud bq` (which covers only BigQuery *Migration
  Service* workflows). All 26 commands are documented in
  [`bq-cli/SKILL.md`](bq-cli/SKILL.md) — including global flags, workflows, and
  the legacy-SQL default gotcha (always pass `--nouse_legacy_sql` for GoogleSQL).
- **`gsutil`** — the **legacy** Cloud Storage CLI. Prefer `gcloud storage` (faster, actively
  developed); see [`storage/SKILL.md`](storage/SKILL.md) for the gsutil→gcloud
  storage transition notes.
- **`kubectl`** — Kubernetes operations on GKE clusters. Install with
  `gcloud components install kubectl gke-gcloud-auth-plugin`, then bridge auth with
  `gcloud container clusters get-credentials CLUSTER --region REGION`. See
  [`container/SKILL.md`](container/SKILL.md).
- **`cbt`** — Bigtable CLI (`gcloud components install cbt`).

---

## General gcloud conventions

These behaviors apply across every `gcloud` command. (Run `gcloud topic <name>` locally for
the authoritative deep-dive on any of these — e.g. `gcloud topic formats`, `gcloud topic filters`;
the full topic list is in [`topic/index.md`](topic/index.md).)

### Global flags (available on every command)

```
--project=PROJECT_ID              Override the active project for this command
--account=ACCOUNT                 Use a specific authenticated account
--impersonate-service-account=SA  Run as a service account via short-lived credentials
--billing-project=PROJECT_ID      Project to bill/quota for user-project-enabled APIs
--configuration=NAME              Use a named gcloud configuration
--format=FORMAT                   Output format (see below)
--filter=EXPRESSION               Client-side resource filtering (see below)
--sort-by=FIELDS                  Sort list output by resource fields (e.g. --sort-by=~creationTimestamp)
--limit=N                         Max resources to list
--page-size=N                     Server page size for list calls
--quiet, -q                       Disable interactive prompts; accept defaults (use in scripts)
--verbosity=LEVEL                 debug|info|warning|error|critical (default warning)
--flags-file=YAML                 Read flags from a YAML file
--flatten=KEY                     Flatten a repeated/nested field into separate records
--log-http                        Log raw HTTP requests/responses (debugging)
--user-output-enabled=false       Suppress normal output (keep --format output)
--help                            Full help for the command
```

### Output formats (`--format`)

By default gcloud pretty-prints. Override with `--format`:

```bash
gcloud compute instances list --format=json          # full JSON (machine-readable)
gcloud compute instances list --format=yaml          # YAML
gcloud compute instances list --format=text          # flat key: value lines (great for discovering field names)
gcloud compute instances list --format='table(name, zone, status)'   # custom table columns
gcloud compute instances list --format='value(name)'                 # bare values, one per line (scripting)
gcloud compute instances list --format='csv(name,zone,status)'       # CSV
```

- `value(...)` is the scripting workhorse — no headers, tab/newline separated:
  ```bash
  for i in $(gcloud compute instances list --format='value(name)'); do echo "$i"; done
  ```
- Discover available fields with `--format=text` or `--format=json` on a single resource:
  ```bash
  gcloud compute instances list --limit=1 --format=text
  ```
- Format attributes/transforms exist too, e.g. `--format='table(name, creationTimestamp.date())'`.

### Filtering (`--filter`)

Client-side selection of listed resources. Combine with `AND`, `OR`, `NOT`, parentheses.

```bash
gcloud compute instances list --filter="machineType:f1-micro"          # field contains
gcloud compute instances list --filter="zone ~ us"                     # regex match (~)
gcloud compute instances list --filter="status=RUNNING"                # equality
gcloud compute instances list --filter="tags.items=(web,prod)"         # any of
gcloud compute instances list --filter="tags.items=web AND -status=TERMINATED"
gcloud compute instances list --filter="creationTimestamp>2024-01-01"
```

Operators: `:` (contains/has-key), `=`/`!=`, `<`/`<=`/`>`/`>=`, `~`/`!~` (regex). `--filter` is
applied by the client after retrieval; some commands also support a server-side filter flag.

### Projects, regions, and configurations

```bash
gcloud config set project MY_PROJECT          # default project for all commands
gcloud config set compute/region us-central1  # default region
gcloud config set compute/zone us-central1-a  # default zone
gcloud config list                            # show active config
gcloud config configurations create staging   # named config (switch with --configuration or activate)
gcloud config configurations activate staging
```

Precedence: explicit `--project`/`--region`/`--zone` flag → active configuration property →
environment variable (`CLOUDSDK_CORE_PROJECT`, `CLOUDSDK_COMPUTE_REGION`, …).

### Authentication

```bash
gcloud auth login                              # user login (browser)
gcloud auth list                               # show credentialed accounts; * marks active
gcloud auth application-default login          # set up Application Default Credentials (ADC) for client libraries/Terraform
gcloud auth activate-service-account --key-file=key.json   # authenticate as a service account
gcloud auth print-access-token                 # short-lived OAuth token (e.g. for curl)
```

Prefer `--impersonate-service-account=SA@PROJECT.iam.gserviceaccount.com` over downloading
service-account keys when possible.

### Enabling APIs

Most services require their API to be enabled on the project first:

```bash
gcloud services enable compute.googleapis.com
gcloud services list --enabled
```

Each service `SKILL.md` notes the API to enable.

### Scripting and automation (agent-relevant)

```bash
set -euo pipefail
PROJECT=$(gcloud config get-value project)
gcloud ... --quiet --format='value(...)'        # no prompts, parseable output
```

Google's official scripting guidance (`cloud.google.com/sdk/docs/scripting-gcloud`) distilled:

- **The exit status is the only reliable error signal.** Non-zero means an error occurred and
  output may be incomplete — check `$?` or rely on `set -e`.
- **Never parse stderr** — human-readable message wording can change between SDK versions.
- **Never parse the default (unformatted) stdout** — it can also change. Always pin the shape
  with `--format=json|yaml|csv|text|value(...)` when a script or agent consumes the output.
- **Disable prompts in non-interactive runs.** `--quiet` auto-accepts defaults; equivalently set
  the property `gcloud config set disable_prompts true` or the env var
  `CLOUDSDK_CORE_DISABLE_PROMPTS=1`. Prompts that *require* input then raise an error instead of
  hanging.
- **Do not run multiple `gcloud` commands in parallel** — officially unsupported (shared
  config/credential state can corrupt). Serialize calls; if concurrent invocations are
  unavoidable, give each process its own config directory via the `CLOUDSDK_CONFIG` env var.
- **Every property has an env-var form**: `CLOUDSDK_<SECTION>_<PROPERTY>` — e.g.
  `CLOUDSDK_CORE_PROJECT`, `CLOUDSDK_COMPUTE_REGION`, `CLOUDSDK_CORE_DISABLE_PROMPTS`. Useful for
  per-invocation overrides in CI without touching the active configuration.
- **Production automation should authenticate as a service account**
  (`gcloud auth activate-service-account --key-file=KEY` or, better, workload identity /
  `--impersonate-service-account`) rather than a user login.
- Many long-running commands accept `--async` (return immediately with an operation) and have a
  matching `operations` subgroup or `--wait`/`wait` command to poll for completion.

### Troubleshooting common failures

- **`PERMISSION_DENIED` / 403 mentioning the API** (e.g. "API has not been used in project …" /
  `SERVICE_DISABLED`): enable it — `gcloud services enable <api>.googleapis.com`. Each service
  `SKILL.md` names the API to enable.
- **`PERMISSION_DENIED` on a resource**: wrong project or missing IAM role. Check
  `gcloud config get-value project`, then inspect with `gcloud projects get-iam-policy PROJECT`
  or diagnose with `gcloud policy-intelligence troubleshoot-policy iam` (see
  [`policy-intelligence/SKILL.md`](policy-intelligence/SKILL.md)).
- **`RESOURCE_EXHAUSTED` / quota exceeded**: regional/project quota. List usage with
  `gcloud compute regions describe REGION` (compute) or the console Quotas page; request
  increases there.
- **Auth/env problems**: `gcloud info --run-diagnostics` checks network reachability and config;
  `gcloud auth list` shows which account is active.
- **Debugging any request**: add `--log-http` (full HTTP traffic) and/or `--verbosity=debug`.

### Release tracks: GA / beta / alpha

The same command often exists on multiple tracks:

```bash
gcloud compute instances create ...        # GA  (documented in this skill)
gcloud beta compute instances create ...   # beta: newer features, may change
gcloud alpha compute instances create ...  # alpha: earliest, may change/break
```

This skill documents the **GA** surface. When a capability is beta/alpha-only, the service
SKILL.md says so; prepend `beta` or `alpha` to the command (install the component if prompted).

## Sourcing & accuracy

All command and flag data is generated directly from the gcloud CLI's own help system (`gcloud <command> --help`, the canonical source Google publishes at `cloud.google.com/sdk/gcloud/reference`), pinned to the installed SDK version. Per-service conceptual docs, quickstarts, and how-to guides are linked from each service's `SKILL.md` and `sources.md` (official `cloud.google.com` sources only).

**Version pinning:** the bulk of the reference was generated against **Google Cloud SDK 552.0.0** (January 2026). The service index was re-audited against **SDK 575.0.0** (June 30, 2026): services new to GA since 552 — `agent-registry`, `apihub`, `biglake`, `datalineage`, `service-health`, `vector-search`, `workload-identity` — are documented from the current published reference at `docs.cloud.google.com/sdk/gcloud/reference`, and `immersive-stream` is flagged as removed. For any flag-level question where exactness matters, `gcloud <command> --help` on the user's installed SDK is always the final authority — prefer it over this reference if they disagree.
