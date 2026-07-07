---
name: gcloud-dataproc
description: >-
  Dataproc via gcloud (`gcloud dataproc`). Create and manage Google Cloud Dataproc clusters and jobs — autoscaling-policies, batches, clusters, jobs, node-groups, operations, workflow-templates.
---

# gcloud dataproc — Dataproc

## Overview

`gcloud dataproc` manages **Dataproc**, Google Cloud's fully managed service for running Apache Spark, Hadoop, Flink, Hive, Pig, Presto, and Trino workloads. Use it to spin up ephemeral or long-lived **clusters**, submit **jobs** to those clusters, run no-cluster **batches** on Dataproc Serverless for Spark, and orchestrate DAGs of jobs with **workflow-templates**. Reach for it when you need managed big-data processing without operating Spark/Hadoop infrastructure yourself. Almost every command is regional — pass `--region` (or set `dataproc/region`) on each invocation.

## Quick reference — common workflows

### 1. Enable the API and create a cluster

```bash
gcloud services enable dataproc.googleapis.com

gcloud dataproc clusters create my-cluster \
    --region=us-central1 \
    --master-machine-type=n4-standard-4 \
    --worker-machine-type=n4-standard-4 \
    --num-workers=2 \
    --optional-components=JUPYTER \
    --enable-component-gateway

gcloud dataproc clusters list --region=us-central1
gcloud dataproc clusters describe my-cluster --region=us-central1
```

### 2. Submit a Spark job to a cluster and stream its output

```bash
gcloud dataproc jobs submit spark \
    --cluster=my-cluster \
    --region=us-central1 \
    --class=org.apache.spark.examples.SparkPi \
    --jars=file:///usr/lib/spark/examples/jars/spark-examples.jar \
    -- 1000

# Watch / re-attach to a running job, and list active jobs on a cluster
gcloud dataproc jobs wait JOB_ID --region=us-central1
gcloud dataproc jobs list --region=us-central1 \
    --cluster=my-cluster --state-filter=active
```

### 3. Submit a PySpark job with extra Python deps and properties

```bash
gcloud dataproc jobs submit pyspark gs://my-bucket/my_script.py \
    --cluster=my-cluster \
    --region=us-central1 \
    --py-files=gs://my-bucket/helpers.zip \
    --properties=spark.executor.memory=4g \
    -- --input=gs://my-bucket/input --output=gs://my-bucket/output
```

### 4. Run a Serverless batch (no cluster required)

```bash
gcloud dataproc batches submit pyspark gs://my-bucket/my_job.py \
    --batch=my-batch-job \
    --region=us-central1 \
    --deps-bucket=gs://my-bucket \
    --service-account=my-sa@my-project.iam.gserviceaccount.com \
    --properties=spark.executor.instances=4 \
    --ttl=2h

gcloud dataproc batches describe my-batch-job --region=us-central1
gcloud dataproc batches wait my-batch-job --region=us-central1
```

### 5. Scale, stop/start, and delete a cluster

```bash
gcloud dataproc clusters update my-cluster --region=us-central1 --num-workers=5
gcloud dataproc clusters stop my-cluster --region=us-central1     # pause to save cost
gcloud dataproc clusters start my-cluster --region=us-central1    # resume later
gcloud dataproc clusters delete my-cluster --region=us-central1
```

### 6. Build and run a workflow template

```bash
gcloud dataproc workflow-templates create my-workflow --region=us-central1

# Attach a managed (ephemeral) cluster that exists only for the workflow run
gcloud dataproc workflow-templates set-managed-cluster my-workflow \
    --region=us-central1 \
    --cluster-name=wf-cluster \
    --num-workers=2 \
    --worker-machine-type=n4-standard-4

# Add a PySpark step, then instantiate (run) the DAG
gcloud dataproc workflow-templates add-job pyspark gs://my-bucket/job.py \
    --step-id=step-1 \
    --workflow-template=my-workflow \
    --region=us-central1

gcloud dataproc workflow-templates instantiate my-workflow --region=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `dataproc autoscaling-policies` | [`autoscaling-policies.md`](autoscaling-policies.md) | 7 | create and manage Dataproc autoscaling policies |
| `dataproc batches` | [`batches.md`](batches.md) | 9 | submit Dataproc batch jobs (Serverless for Spark) |
| `dataproc clusters` | [`clusters.md`](clusters.md) | 13 | create and manage Dataproc clusters |
| `dataproc jobs` | [`jobs.md`](jobs.md) | 18 | submit and manage Dataproc jobs |
| `dataproc node-groups` | [`node-groups.md`](node-groups.md) | 2 | manage Dataproc node groups |
| `dataproc operations` | [`operations.md`](operations.md) | 6 | view and manage Dataproc operations |
| `dataproc workflow-templates` | [`workflow-templates.md`](workflow-templates.md) | 24 | create and manage Dataproc workflow templates |

See [`index.md`](index.md) for a one-line index of all 79 GA commands.

## Common flags & tips

- **`--region` is required almost everywhere.** Dataproc regions are independent namespaces. Either pass `--region=us-central1` on each command or set a default with `gcloud config set dataproc/region us-central1`. A few resources also accept `--zone`/`-z` on cluster create.
- **`--async`** returns immediately on create/delete/start/stop/update/import operations instead of blocking; pair it with `gcloud dataproc operations wait`/`describe` to track progress.
- **`--properties=PREFIX:PROPERTY=VALUE`** sets engine config on cluster create (e.g. `--properties=spark:spark.executor.memory=4g`, `hdfs:...`, `yarn:...`). On `jobs submit` / `batches submit` the form is just `--properties=PROPERTY=VALUE`.
- **Job args** go after a `--` separator: `... --jars=... -- 1000`.
- **Clusters vs. batches:** cluster jobs (`jobs submit ...`) run on a cluster you manage; batches (`batches submit ...`) are Serverless — no cluster, use `--deps-bucket` for dependencies and `--ttl` to bound runtime.
- **Cost control:** `clusters stop`/`start` pauses billing for idle clusters; `clusters create --delete-max-idle=2h` / `--stop-max-idle=30m` auto-deletes/stops idle clusters.
- **Filtering / formatting** (server-side filters are case-sensitive):
  - `gcloud dataproc clusters list --region=us-central1 --filter='status.state = ACTIVE'`
  - `gcloud dataproc jobs list --region=us-central1 --filter='status.state = ACTIVE AND labels.env = staging'`
  - `gcloud dataproc jobs list --region=us-central1 --format='table(reference.jobId, status.state)'`
- **Autoscaling policies** have no `create` verb — author a YAML and apply it with `gcloud dataproc autoscaling-policies import`, then attach via `clusters create --autoscaling-policy=...`.
- **Export/import** clusters, workflow-templates, and autoscaling-policies to/from YAML for reproducible, version-controlled configs.

## beta / alpha

`gcloud beta dataproc` adds two command groups not present in GA:

- **`gcloud beta dataproc sessions`** — interactive Spark sessions (`create`, `create spark`, `delete`, `describe`, `list`, `terminate`).
- **`gcloud beta dataproc session-templates`** — manage session templates (`create`, `delete`, `describe`, `export`, `import`, `list`).

`gcloud alpha dataproc` exists for early-access features. (The `batches` group debuted in beta but is now fully GA.)

## Official documentation

- Dataproc product docs home: https://cloud.google.com/dataproc/docs
- Dataproc Serverless docs (batches): https://cloud.google.com/dataproc-serverless/docs
- Product overview — clusters, jobs, batches, workflows: https://cloud.google.com/dataproc/docs/concepts/overview
- gcloud quickstart (enable API, create cluster, submit job, delete): https://cloud.google.com/dataproc/docs/quickstarts/quickstart-gcloud
- How-to: create clusters: https://cloud.google.com/dataproc/docs/guides/create-cluster
- How-to: submit jobs (Spark, PySpark, Hadoop, Hive, Pig): https://cloud.google.com/dataproc/docs/guides/submit-job
- Workflow templates (DAG orchestration): https://cloud.google.com/dataproc/docs/concepts/workflows/overview
- Cluster configuration properties (spark:, hdfs:, yarn:, ...): https://cloud.google.com/dataproc/docs/concepts/configuring-clusters/cluster-properties
- IAM roles for Dataproc: https://cloud.google.com/dataproc/docs/concepts/iam
- gcloud CLI reference: https://cloud.google.com/sdk/gcloud/reference/dataproc
