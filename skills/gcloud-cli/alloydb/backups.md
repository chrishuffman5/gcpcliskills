# gcloud alloydb backups

provide commands for managing AlloyDB backups

### `gcloud alloydb backups create`

Creates a new AlloyDB backup within a given project

Creates a new AlloyDB backup within a given project.

**Synopsis:**
```
gcloud alloydb backups create BACKUP --cluster=CLUSTER --region=REGION
    [--async] [--tags=[KEY=VALUE,...]]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKUP
   The AlloyDB backup to create. This must either be the backup ID
   (myBackup) or the full backup path
   (projects/myProject/locations/us-central1/backups/myBackup). In the
   first case, the project and location are assumed to be the same as the
   cluster being backed up. The second form can be used to create
   cross-region and cross-project backups.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | AlloyDB cluster ID |
| `--region` | REGION |  | The region of the cluster to backup. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--tags` | [KEY=VALUE,...] |  | List of tags KEY=VALUE pairs to bind. Each item must be expressed as <tag-key-namespaced-name>=<tag-value-short-name>. Example: 123/environment=production,123/costCenter=marketing |


**Examples:**
```bash
To create a new backup, run:

    $ gcloud alloydb backups create my-backup --cluster=my-cluster \
        --region=us-central1

To create a new cross-region backup, run:

    $ gcloud alloydb backups create \
        projects/my-project/locations/us-west1/backups/my-backup \
        --cluster=my-cluster --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/backups/create)

---
### `gcloud alloydb backups delete`

Deletes an AlloyDB backup within a given project

Deletes an AlloyDB backup within a given project.

**Synopsis:**
```
gcloud alloydb backups delete BACKUP --region=REGION [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKUP
   AlloyDB backup ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a backup, run:

    $ gcloud alloydb backups delete my-backup --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/backups/delete)

---
### `gcloud alloydb backups describe`

Describes an AlloyDB backup in a given project and region

Describes an AlloyDB backup in a given project and region.

**Synopsis:**
```
gcloud alloydb backups describe BACKUP --region=REGION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKUP
   AlloyDB backup ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Examples:**
```bash
To describe a backup, run:

    $ gcloud alloydb backups describe my-backup --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/backups/describe)

---
### `gcloud alloydb backups list`

Lists AlloyDB backups in a given project

Lists AlloyDB backups in a given project in the alphabetical order of the
backup name.

**Synopsis:**
```
gcloud alloydb backups list [--region=REGION; default="-"]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION | - | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. Default: list clusters in all regions. |


**Examples:**
```bash
To list backups, run:

    $ gcloud alloydb backups list --region=us-central1

Use the --format flag to customize the fields that are outputted. For
example, to list backups with their names and sizes, run:

    $ gcloud alloydb backups list --region=us-central1 \
        --format="table(name, size_bytes)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/backups/list)

---