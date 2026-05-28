# gcloud colab — Colab Enterprise

## Overview
`gcloud colab` manages Colab Enterprise, a managed, collaborative notebook environment that runs Jupyter/Colab notebooks on Google Cloud with enterprise security and IAM. Its API is a subset of the Vertex AI API. Reach for it to provision notebook compute (runtimes) from reusable VM blueprints (runtime templates), and to run notebooks headlessly as one-off executions or on recurring cron schedules. All resources are regional, so most commands take `--region` (or default it with `gcloud config set colab/region`).

## Quick reference — common workflows

### 1. Enable APIs and set a default region
```bash
gcloud services enable aiplatform.googleapis.com dataform.googleapis.com compute.googleapis.com
gcloud config set colab/region us-central1
```

### 2. Create a runtime template (the VM blueprint)
```bash
# Minimal template (defaults: e2-standard-4, 100 GB PD_STANDARD disk)
gcloud colab runtime-templates create \
    --display-name=my-runtime-template \
    --region=us-central1

# Template with a GPU accelerator
gcloud colab runtime-templates create \
    --display-name=my-gpu-template \
    --machine-type=n1-standard-2 \
    --accelerator-type=NVIDIA_TESLA_V100 \
    --accelerator-count=1 \
    --region=us-central1

gcloud colab runtime-templates list --region=us-central1
```

### 3. Create and manage a runtime (the running VM)
```bash
gcloud colab runtimes create \
    --display-name=my-runtime \
    --runtime-template=my-runtime-template \
    --region=us-central1

gcloud colab runtimes stop my-runtime --region=us-central1     # stop to save cost
gcloud colab runtimes start my-runtime --region=us-central1    # restart
gcloud colab runtimes upgrade my-runtime --region=us-central1  # upgrade the image
gcloud colab runtimes delete my-runtime --region=us-central1
```

### 4. Run a one-off notebook execution (headless)
```bash
gcloud colab executions create \
    --display-name=my-execution \
    --notebook-runtime-template=my-runtime-template \
    --gcs-notebook-uri=gs://my-bucket/my-notebook.ipynb \
    --service-account=my-sa@my-project.iam.gserviceaccount.com \
    --gcs-output-uri=gs://my-bucket/results \
    --region=us-central1

gcloud colab executions describe my-execution --region=us-central1
gcloud colab executions list --region=us-central1
```

### 5. Schedule a recurring notebook run
```bash
gcloud colab schedules create \
    --display-name=my-schedule \
    --cron-schedule='TZ=America/Los_Angeles 0 8 * * *' \
    --max-concurrent-runs=1 \
    --start-time=2026-07-01T00:00:00Z \
    --execution-display-name=my-execution \
    --notebook-runtime-template=my-runtime-template \
    --gcs-notebook-uri=gs://my-bucket/my-notebook.ipynb \
    --service-account=my-sa@my-project.iam.gserviceaccount.com \
    --gcs-output-uri=gs://my-bucket/results \
    --region=us-central1

gcloud colab schedules pause my-schedule --region=us-central1
gcloud colab schedules resume my-schedule --region=us-central1
gcloud colab schedules update my-schedule \
    --cron-schedule='TZ=America/Los_Angeles 0 9 * * *' \
    --max-runs=10 \
    --region=us-central1
```

### 6. Grant per-template access to a user
```bash
gcloud colab runtime-templates add-iam-policy-binding my-runtime-template \
    --region=us-central1 \
    --member=user:someone@example.com \
    --role=roles/aiplatform.notebookRuntimeUser

gcloud colab runtime-templates get-iam-policy my-runtime-template --region=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `colab executions` | [`executions.md`](executions.md) | 4 | manage Colab Enterprise notebook execution jobs |
| `colab runtime-templates` | [`runtime-templates.md`](runtime-templates.md) | 8 | manage Colab Enterprise runtime templates |
| `colab runtimes` | [`runtimes.md`](runtimes.md) | 7 | manage Colab Enterprise runtimes |
| `colab schedules` | [`schedules.md`](schedules.md) | 7 | manage Colab Enterprise notebook execution schedules |

See [`index.md`](index.md) for a one-line index of all 26 commands.

## Common flags & tips
- **Region is required (or defaulted).** Most commands take `--region`; set a default with `gcloud config set colab/region us-central1` to omit it. The `colab/region` property backs every resource's region attribute.
- **Resource identity.** Templates, runtimes, executions, and schedules are addressed by ID. For `runtime-templates create` and `runtimes create` you may pin the ID with `--runtime-template-id` / `--runtime-id`; otherwise a random ID is generated.
- **Notebook source (executions & schedules).** Provide the notebook one way: `--gcs-notebook-uri` (Cloud Storage, optionally `--generation`), a Dataform repo (`--dataform-repository-name` with `--commit-sha`), or `--direct-content` (executions only). Pair it with `--gcs-output-uri` for results and an identity (`--service-account` or `--user-email`).
- **Execution timeout.** `--execution-timeout` defaults to `24h`; accepts duration strings (see `gcloud topic datetimes`).
- **Runtime template sizing & security.** `--machine-type` (default `e2-standard-4`), `--disk-size-gb` (100), `--disk-type` (`PD_STANDARD`), `--accelerator-type`/`--accelerator-count`, `--idle-shutdown-timeout` (`3h`), plus `--enable-secure-boot`, `--no-enable-euc` (disable end-user credentials), `--no-enable-internet-access`, `--network`/`--subnetwork`, `--network-tags`, and CMEK via `--kms-key`.
- **Long-running ops.** `create`/`delete`/`start`/`stop`/`upgrade` accept `--async` to return immediately.
- **Cron timezones.** Prefix the cron string with `TZ=` or `CRON_TZ=` plus an IANA zone, e.g. `'TZ=America/Los_Angeles 0 8 * * *'`. Schedules end at `--end-time` or after `--max-runs`; control concurrency with `--max-concurrent-runs` and queueing with `--enable-queueing`. `schedules resume` can backfill missed runs with `--enable-catch-up`.
- **Listing.** `list` commands support `--filter`, `--limit`, `--page-size`, `--sort-by`, and `--uri`. Example: `gcloud colab runtimes list --region=us-central1 --filter="displayName:my-*" --sort-by=createTime`.
- **Template IAM.** Grant per-template access with `add-iam-policy-binding`/`remove-iam-policy-binding` (`--member`, `--role`), inspect with `get-iam-policy`, or apply a file with `set-iam-policy POLICY_FILE`. `roles/aiplatform.notebookRuntimeUser` lets a principal create runtimes from that template.

## beta / alpha
`gcloud beta colab` mirrors the GA surface — the same four subgroups (`executions`, `runtime-templates`, `runtimes`, `schedules`) with no documented beta-only commands. No `gcloud alpha colab` surface exists. Prefer GA (`gcloud colab`) for all documented commands.

## Official documentation
- [Colab Enterprise docs home](https://cloud.google.com/colab/docs) — getting started, guides, and resource concepts.
- [Introduction](https://cloud.google.com/colab/docs/introduction) — what Colab Enterprise is and how it relates to Vertex AI.
- [Quickstart](https://cloud.google.com/colab/docs/quickstart) — enable APIs, create a notebook, run code, manage notebooks.
- [Access control (IAM)](https://cloud.google.com/colab/docs/access-control) — Colab Enterprise admin/user roles and underlying Vertex AI roles.
- [Create a runtime template](https://cloud.google.com/colab/docs/create-runtime-template) — machine type, accelerators, disk, networking, and security options.
- [Manage runtimes](https://cloud.google.com/colab/docs/manage-runtimes) — start, stop, disconnect, reconnect, and delete runtimes.
- [gcloud colab CLI reference](https://cloud.google.com/sdk/gcloud/reference/colab) — full command/flag reference for all four groups.
