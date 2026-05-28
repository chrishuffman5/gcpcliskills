# gcloud healthcare — Cloud Healthcare API

## Overview

The Cloud Healthcare API is a managed service for storing, processing, and accessing healthcare data in standard formats — FHIR, HL7v2, and DICOM — on Google Cloud. The resource hierarchy is **Project → Dataset → Store(s)**: a dataset is a regional container, and each dataset holds one or more typed stores (FHIR, DICOM, HL7v2, or consent stores). Reach for `gcloud healthcare` to provision datasets and stores, import/export clinical data to and from Cloud Storage or BigQuery, de-identify PHI, manage per-resource IAM, and track the long-running operations these tasks produce.

## Quick reference — common workflows

### Create a dataset and inspect it
```bash
# One-time: enable the API
gcloud services enable healthcare.googleapis.com

# Optional: set a default location so you can omit --location everywhere
gcloud config set healthcare/location us-central1

gcloud healthcare datasets create my-dataset --location=us-central1
gcloud healthcare datasets describe my-dataset --location=us-central1
gcloud healthcare datasets list --location=us-central1
```

### Create a FHIR R4 store and move data in/out
```bash
# Create an R4 store (version is required and immutable)
gcloud healthcare fhir-stores create my-fhir-store \
    --dataset=my-dataset --location=us-central1 --version=r4

# Import newline-delimited FHIR JSON from Cloud Storage (async LRO)
gcloud healthcare fhir-stores import gcs my-fhir-store \
    --dataset=my-dataset --location=us-central1 \
    --gcs-uri=gs://my-bucket/fhir-data/*.ndjson --async

# Export back to Cloud Storage
gcloud healthcare fhir-stores export gcs my-fhir-store \
    --dataset=my-dataset --location=us-central1 \
    --gcs-uri=gs://my-bucket/fhir-export/

# Export to BigQuery using the analytics schema
gcloud healthcare fhir-stores export bq my-fhir-store \
    --dataset=my-dataset --location=us-central1 \
    --bq-dataset=bq://my-project.my_bq_dataset --schema-type=analytics
```

### Create a DICOM store and import/export images
```bash
gcloud healthcare dicom-stores create my-dicom-store \
    --dataset=my-dataset --location=us-central1

# Import DICOM objects (** recurses into sub-folders)
gcloud healthcare dicom-stores import gcs my-dicom-store \
    --dataset=my-dataset --location=us-central1 \
    --gcs-uri="gs://my-bucket/dicom/**" --async

# Export to Cloud Storage in original DICOM format
gcloud healthcare dicom-stores export gcs my-dicom-store \
    --dataset=my-dataset --location=us-central1 \
    --gcs-uri-prefix=gs://my-bucket/dicom-export/ \
    --mime-type=application/dicom

gcloud healthcare dicom-stores metrics my-dicom-store \
    --dataset=my-dataset --location=us-central1
```

### Create an HL7v2 store with Pub/Sub notifications and import messages
```bash
# Create a v2-parser store with a notification topic (topic must exist first)
gcloud healthcare hl7v2-stores create my-hl7v2-store \
    --dataset=my-dataset --location=us-central1 --parser-version=v2 \
    --notification-config=pubsub-topic=projects/my-project/topics/my-topic

gcloud healthcare hl7v2-stores import gcs my-hl7v2-store \
    --dataset=my-dataset --location=us-central1 \
    --gcs-uri=gs://my-bucket/hl7v2-messages/ --async

# Export raw messages only
gcloud healthcare hl7v2-stores export gcs my-hl7v2-store \
    --dataset=my-dataset --location=us-central1 \
    --gcs-uri=gs://my-bucket/hl7v2-export/ --message-view=raw-only
```

### De-identify a whole dataset, then monitor the operation
```bash
# Destination dataset must NOT already exist
gcloud healthcare datasets deidentify my-dataset --location=us-central1 \
    --destination-dataset=projects/my-project/locations/us-central1/datasets/my-deid-dataset \
    --default-fhir-config \
    --dicom-filter-tags=MediaStorageSOPClassUID,SeriesInstanceUID,StudyInstanceUID \
    --async

gcloud healthcare operations list --dataset=my-dataset --location=us-central1
gcloud healthcare operations describe OPERATION_ID \
    --dataset=my-dataset --location=us-central1
```

### Grant and inspect IAM on a single FHIR store
```bash
gcloud healthcare fhir-stores add-iam-policy-binding my-fhir-store \
    --dataset=my-dataset --location=us-central1 \
    --member="serviceAccount:my-sa@my-project.iam.gserviceaccount.com" \
    --role="roles/healthcare.fhirStoreAdmin"

gcloud healthcare fhir-stores get-iam-policy my-fhir-store \
    --dataset=my-dataset --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `healthcare consent-stores` | [`consent-stores.md`](consent-stores.md) | 12 | manage consent stores; check/evaluate user consents and accessible data |
| `healthcare datasets` | [`datasets.md`](datasets.md) | 10 | create/update/list/delete datasets, manage dataset IAM, and de-identify |
| `healthcare dicom-stores` | [`dicom-stores.md`](dicom-stores.md) | 14 | manage DICOM stores; import/export (GCS & BigQuery), metrics, de-identify |
| `healthcare fhir-stores` | [`fhir-stores.md`](fhir-stores.md) | 14 | manage FHIR stores; import/export (GCS & BigQuery), metrics, de-identify |
| `healthcare hl7v2-stores` | [`hl7v2-stores.md`](hl7v2-stores.md) | 12 | manage HL7v2 stores; import/export (GCS), notifications, metrics |
| `healthcare operations` | [`operations.md`](operations.md) | 2 | describe and list long-running operations |

See [`index.md`](index.md) for a one-line index of all 64 commands.

## Common flags & tips

- **Location is required.** Every command needs `--location` (e.g. `us-central1`, `europe-west2`). Set it once with `gcloud config set healthcare/location LOCATION` to drop the flag from subsequent commands.
- **Store commands need `--dataset`.** All `*-stores` commands take the store ID plus `--dataset=DATASET` (and `--location`). `list` requires `--dataset`; alternatively pass a fully qualified resource name as the positional and the attributes are inferred.
- **`--version` for FHIR is immutable.** `fhir-stores create` requires `--version` (one of `dstu2`, `stu3`, `r4`); it cannot be changed after creation.
- **Long-running tasks support `--async`.** `create` (datasets), `import`, `export`, and `deidentify` all accept `--async` to return immediately and return an operation you track with `gcloud healthcare operations describe/list`.
- **De-identify destinations differ.** `datasets deidentify --destination-dataset=...` requires a dataset that does **not** yet exist; `fhir-stores`/`dicom-stores deidentify --destination-store=...` require a store that **already** exists.
- **BigQuery export targets.** FHIR uses `--bq-dataset=bq://PROJECT.DATASET` with `--schema-type` (`analytics` / `analytics_v2`); DICOM uses `--bq-table=bq://PROJECT.DATASET.TABLE`. Both accept `--write-disposition` (`write-append` / `write-empty` / `write-truncate`).
- **GCS wildcards on import.** `*` matches non-separator characters, `**` recurses into sub-folders (use at end of path), `?` matches a single character — quote URIs containing wildcards.
- **Useful `--format` / `--filter`:** list outputs support standard flags, e.g.
  ```bash
  gcloud healthcare fhir-stores list --dataset=my-dataset --location=us-central1 \
      --format="table(name, version)"
  gcloud healthcare operations list --dataset=my-dataset --location=us-central1 \
      --filter="done=false"
  ```
- **IAM scope.** Bindings can be set at the dataset level (`datasets add-iam-policy-binding`) or per store (`fhir-stores`/`dicom-stores`/`hl7v2-stores`/`consent-stores add-iam-policy-binding`). Healthcare predefined roles include `roles/healthcare.datasetAdmin`, `roles/healthcare.fhirStoreAdmin`, `roles/healthcare.fhirResourceEditor`, `roles/healthcare.dicomStoreAdmin`, and `roles/healthcare.hl7V2StoreAdmin`.

## beta / alpha

Both `gcloud beta healthcare` and `gcloud alpha healthcare` exist and mirror the six GA subgroups (subject to change). The notable beta-only addition is:

- **`gcloud beta healthcare nlp analyze-entities`** — the Cloud Healthcare Natural Language API; finds and analyzes medical entities in a document. Not present in GA.

## Official documentation

- [Cloud Healthcare API documentation](https://cloud.google.com/healthcare-api/docs) — product docs home (concepts, hierarchy, data models).
- [Quickstart](https://cloud.google.com/healthcare-api/docs/quickstart) — enable the API, grant roles, create a dataset and stores.
- [How-to: datasets](https://cloud.google.com/healthcare-api/docs/how-tos/datasets) — create, update, describe, list, and delete datasets.
- [How-to: FHIR stores](https://cloud.google.com/healthcare-api/docs/how-tos/fhir) — create and manage FHIR stores (DSTU2/STU3/R4).
- [Access control](https://cloud.google.com/healthcare-api/docs/access-control) — IAM roles and permissions for every Healthcare resource type.
- [gcloud healthcare CLI reference](https://cloud.google.com/sdk/gcloud/reference/healthcare) — full reference for all GA subgroups.
- [gcloud beta healthcare reference](https://cloud.google.com/sdk/gcloud/reference/beta/healthcare) — beta surface, including the `nlp` subgroup.
