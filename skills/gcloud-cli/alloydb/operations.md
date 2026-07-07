# gcloud alloydb operations

provide commands for managing AlloyDB operations

### `gcloud alloydb operations cancel`

Cancels an AlloyDB operation

Cancels an AlloyDB operation.

**Synopsis:**
```
gcloud alloydb operations cancel OPERATION --region=REGION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION
   AlloyDB operation ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Examples:**
```bash
To cancel an operation, run:

    $ gcloud alloydb operations cancel operation-123456789 \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/operations/cancel)

---
### `gcloud alloydb operations delete`

Deletes an AlloyDB operation

Deletes an AlloyDB operation.

**Synopsis:**
```
gcloud alloydb operations delete OPERATION --region=REGION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION
   AlloyDB operation ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Examples:**
```bash
To delete an operation, run:

    $ gcloud alloydb operations delete operation-123456789 \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/operations/delete)

---
### `gcloud alloydb operations describe`

Describes an AlloyDB operation

Describes an AlloyDB operation.

**Synopsis:**
```
gcloud alloydb operations describe OPERATION --region=REGION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION
   AlloyDB operation ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Examples:**
```bash
To describe an operation, run:

    $ gcloud alloydb operations describe operation-123456789 \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/operations/describe)

---
### `gcloud alloydb operations list`

Lists AlloyDB operations

Lists AlloyDB operations.

**Synopsis:**
```
gcloud alloydb operations list [--cluster=CLUSTER]
    [--region=REGION; default="-"] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | AlloyDB cluster ID |
| `--region` | REGION | - | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. Default: list operations in all regions. |


**Examples:**
```bash
To list operations, run:

    $ gcloud alloydb operations list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/operations/list)

---