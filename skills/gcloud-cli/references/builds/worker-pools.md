# gcloud builds worker-pools

manage worker pools for Google Cloud Build

### `gcloud builds worker-pools create`

Create a worker pool for use by Google Cloud Build

Create a worker pool for use by Google Cloud Build.

**Synopsis:**
```
gcloud builds worker-pools create WORKER_POOL [--region=REGION]
    [--config-from-file=CONFIG_FROM_FILE
      | --worker-disk-size=WORKER_DISK_SIZE
      --worker-machine-type=WORKER_MACHINE_TYPE
      --peered-network=PEERED_NETWORK
      --peered-network-ip-range=PEERED_NETWORK_IP_RANGE --no-public-egress]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
WORKER_POOL
   Unique identifier for the worker pool to create. This value should be
   1-63 characters, and valid characters are [a-z][0-9]-
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Cloud region where the worker pool is created. See https://cloud.google.com/build/docs/locations for available locations. |


**Examples:**
```bash
To create a worker pool named wp1 in region us-central1, run:

    $ gcloud builds worker-pools create wp1 --region=us-central1

To create a worker pool in project p1 in region us-central1 where workers
are of machine type e2-standard-2 and are peered to the VPC network
projects/123/global/networks/default within the IP range 192.168.0.0/28 and
have a disk size of 64GB, run:

    $ gcloud builds worker-pools create wp1 --project=p1 \
        --region=us-central1 \
        --peered-network=projects/123/global/networks/default \
        --peered-network-ip-range=192.168.0.0/28 \
        --worker-machine-type=e2-standard-2 --worker-disk-size=64GB
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/worker-pools/create)

---
### `gcloud builds worker-pools delete`

Delete a worker pool from Cloud Build

Delete a worker pool from Cloud Build.

**Synopsis:**
```
gcloud builds worker-pools delete WORKER_POOL [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
WORKER_POOL
   The ID of the worker pool to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | The Cloud region where the worker pool is. |


**Examples:**
```bash
To delete a worker pool named wp1 in region us-central1, run:

    $ gcloud builds worker-pools delete wp1 --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/worker-pools/delete)

---
### `gcloud builds worker-pools describe`

Describe a worker pool used by Cloud Build

Describe a worker pool used by Cloud Build.

**Synopsis:**
```
gcloud builds worker-pools describe WORKER_POOL [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
WORKER_POOL
   The ID of the worker pool to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | The Cloud region where the worker pool is. |


**Examples:**
```bash
To get information about a worker pool named wp1 in region us-central1,
run:

    $ gcloud builds worker-pools describe wp1 --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/worker-pools/describe)

---
### `gcloud builds worker-pools list`

List all worker pools in a Google Cloud project

List all worker pools in a Google Cloud project.

**Synopsis:**
```
gcloud builds worker-pools list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | The Cloud region to list worker pools in. |


**Examples:**
```bash
To fetch a list of worker pools running in region us-central1, run:

    $ gcloud builds worker-pools list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/worker-pools/list)

---
### `gcloud builds worker-pools update`

Update a worker pool used by Cloud Build

Update a worker pool used by Cloud Build.

**Synopsis:**
```
gcloud builds worker-pools update WORKER_POOL
    (--config-from-file=CONFIG_FROM_FILE | --[no-]public-egress
      --worker-disk-size=WORKER_DISK_SIZE
      --worker-machine-type=WORKER_MACHINE_TYPE) [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
WORKER_POOL
   Unique identifier for the worker pool to update. This value should be
   1-63 characters, and valid characters are [a-z][0-9]-
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config-from-file` | CONFIG_FROM_FILE |  | _[Exactly one of these must be specified:]_ File that contains updates to the configuration for the worker pool. See https://cloud.google.com/build/docs/private-pools/worker-pool-config-file-schema for options. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Cloud region where the worker pool is updated. See https://cloud.google.com/build/docs/locations for available locations. |


**Examples:**
```bash
To change the machine type and disk size of workers in a worker pool named
wp1, run:

    $ gcloud builds worker-pools update wp1 --region=us-central1 \
        --worker-machine-type=e2-standard-2 --worker-disk-size=64GB
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/builds/worker-pools/update)

---