# gcloud composer — Cloud Composer

## Overview

Cloud Composer (branded as **Managed Service for Apache Airflow**) is a fully managed workflow orchestration service built on Apache Airflow. Each *environment* provisions a GKE-backed Airflow stack — scheduler, workers, web server, Airflow metadata database, and a Cloud Storage bucket for DAGs, plugins, and data — so you run native Airflow without managing the infrastructure. Reach for `gcloud composer` to create and size environments, deploy and run DAGs, install PyPI dependencies, and upgrade or snapshot environments. Commands fall into two groups: `composer environments` (the bulk of the surface) and `composer operations` (track long-running async work).

## Quick reference — common workflows

### 1. Enable the API and create an environment

```bash
gcloud services enable composer.googleapis.com

# Create with an explicit image version, size, and node service account
gcloud composer environments create my-env \
    --location=us-central1 \
    --image-version=composer-2-airflow-2 \
    --environment-size=small \
    --service-account=my-sa@PROJECT.iam.gserviceaccount.com
```

### 2. List and describe environments

```bash
# List environments across one or more regions (note: --locations, plural)
gcloud composer environments list --locations=us-central1

# Full details of one environment (note: --location, singular)
gcloud composer environments describe my-env --location=us-central1
```

### 3. Deploy DAGs and trigger a run

```bash
# Import a local DAG file into the environment's dags/ folder in GCS
gcloud composer environments storage dags import my-env \
    --location=us-central1 \
    --source=my_dag.py

# Confirm the upload
gcloud composer environments storage dags list \
    --environment=my-env --location=us-central1

# Trigger a DAG remotely via the Airflow 2 CLI (flags go after --)
gcloud composer environments run my-env --location=us-central1 \
    dags trigger -- my_dag_id

# Inspect runs for that DAG
gcloud composer environments run my-env --location=us-central1 \
    dags list-runs -- --dag-id my_dag_id
```

### 4. Install or update PyPI packages

```bash
# Install/pin a single package
gcloud composer environments update my-env \
    --location=us-central1 \
    --update-pypi-package="scipy>=1.7.0"

# Install from a requirements file
gcloud composer environments update my-env \
    --location=us-central1 \
    --update-pypi-packages-from-file=requirements.txt

# Verify what is installed on a worker
gcloud composer environments list-packages my-env --location=us-central1
```

### 5. Upgrade an environment

```bash
# See the suggested image-version upgrades
gcloud composer environments list-upgrades my-env --location=us-central1

# Pre-flight: confirm the target version has no PyPI conflicts
gcloud composer environments check-upgrade my-env \
    --location=us-central1 --airflow-version=2.9.3

# Apply the upgrade asynchronously, then poll the operation
gcloud composer environments update my-env \
    --location=us-central1 --airflow-version=2.9.3 --async
gcloud composer operations list --locations=us-central1
gcloud composer operations wait OPERATION_ID --location=us-central1
```

### 6. Save and restore a snapshot

```bash
# Save the current environment state to a GCS path
gcloud composer environments snapshots save my-env \
    --location=us-central1 \
    --snapshot-location=gs://my-backup-bucket/snapshots

# Load a specific snapshot back into an environment
gcloud composer environments snapshots load my-env \
    --location=us-central1 \
    --snapshot-path=gs://my-backup-bucket/snapshots/my-env-snapshot-TIMESTAMP
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `composer environments` | [`environments.md`](environments.md) | 37 | Create, configure, run, upgrade, and snapshot environments; manage DAG/data/plugin storage, ConfigMaps, and Secrets |
| `composer operations` | [`operations.md`](operations.md) | 4 | Describe, list, wait on, and delete long-running async operations |

See [`index.md`](index.md) for a one-line index of all 41 commands.

## Common flags & tips

- **Location is required almost everywhere.** Most `environments` commands take `--location=REGION` (singular). The two `list` commands (`environments list`, `operations list`) instead take `--locations=REGION,...` (plural, comma-separated for multiple regions). You can also set a default via `gcloud config set composer/location us-central1`.
- **Async + operations.** Long-running commands (`create`, `update`, `delete`, `check-upgrade`, `restart-web-server`, `database-failover`, `snapshots save/load`) accept `--async` to return immediately. Track the returned operation with `gcloud composer operations describe|wait|list`.
- **`environments run` separator.** The Airflow sub-command goes after the environment/location args; any flags for the sub-command must follow a literal `--`, e.g. `... run my-env --location=us-central1 dags trigger -- my_dag`. Airflow 2 uses two-word sub-commands (`dags trigger`, `dags list`); Airflow 1.10.x uses `trigger_dag`, `list_dags`.
- **`update` takes exactly one change per invocation.** Its mutually-exclusive flag group means you supply one mutation at a time (e.g. `--node-count`, `--environment-size`, `--airflow-version`, `--update-pypi-package`, `--update-labels`/`--remove-labels`, `--update-env-variables`). Run multiple `update` commands for multiple changes.
- **Storage sub-commands.** `storage {dags,data,plugins} {import,export,delete,list}` move files in/out of the environment's GCS bucket. `import` needs `--source`; `export` needs `--destination`; the environment may be passed positionally or via `--environment`, and `--location` is required.
- **Useful formatting / filtering:**
  - `gcloud composer environments list --locations=us-central1 --format="table(name, state, config.softwareConfig.imageVersion)"`
  - `gcloud composer operations list --locations=us-central1 --filter="metadata.operationType=UPDATE" --sort-by=~metadata.createTime`
  - `gcloud composer environments describe my-env --location=us-central1 --format="value(config.dagGcsPrefix)"` to grab the DAGs bucket path.
- **Naming:** environment IDs follow RFC 1035 (lowercase letters, digits, hyphens). You must set `--service-account` explicitly at create time; it cannot be changed later.

## beta / alpha

`gcloud beta composer` and `gcloud alpha composer` expose the same `environments` and `operations` groups as GA. The features the alpha track historically incubated — `user-workloads-config-maps`, `user-workloads-secrets`, `database-failover`, `fetch-database-properties`, `list-workloads` (Composer 3+), and `snapshots load`/`save` — are all now in GA and documented in `environments.md`. There are no beta- or alpha-exclusive sub-commands required for core workflows; use GA (`gcloud composer`) for production.

## Official documentation

- **Product docs home — Cloud Composer overview:** https://cloud.google.com/composer/docs/concepts/overview — what Cloud Composer / Managed Airflow is and its key concepts (DAGs, environments, GKE, storage).
- **gcloud CLI reference:** https://cloud.google.com/sdk/gcloud/reference/composer — authoritative `composer environments` and `composer operations` command/flag reference.
- **Quickstart (Composer 2):** https://cloud.google.com/composer/docs/composer-2/quickstart — enable API, create an environment, upload and run a DAG, clean up.
- **Create environments:** https://cloud.google.com/composer/docs/how-to/managing/creating — all major `create` flags for size, networking, security, and config.
- **Upgrade environments:** https://cloud.google.com/composer/docs/how-to/managing/upgrading — `check-upgrade`, `list-upgrades`, and `update --airflow-version`/`--image-version`.
- **Install Python dependencies:** https://cloud.google.com/composer/docs/composer-2/install-python-dependencies — `--update-pypi-package` and `--update-pypi-packages-from-file`.
- **Manage DAGs:** https://cloud.google.com/composer/docs/composer-2/manage-dags — adding, updating, and deleting DAGs via the `storage dags` sub-commands.
- **Access control (IAM):** https://cloud.google.com/composer/docs/composer-2/access-control — predefined Composer roles and service-account requirements.
