# gcloud compute commitments

manage Compute Engine commitments

### `gcloud compute commitments create`

Create Compute Engine commitments

Create Compute Engine commitments.

**Synopsis:**
```
gcloud compute commitments create COMMITMENT --plan=PLAN
    (--resources=[local-ssd=LOCAL-SSD],[memory=MEMORY],[vcpu=VCPU]
      --resources-accelerator=[count=COUNT],[type=TYPE]) [--auto-renew]
    [--custom-end-time=CUSTOM_END_TIME]
    [--merge-source-commitments=MERGE_SOURCE_COMMITMENTS] [--region=REGION]
    [--split-source-commitment=SPLIT_SOURCE_COMMITMENT]
    [--type=TYPE; default="general-purpose"]
    [--existing-reservation=[name=NAME],[zone=ZONE]
      | --reservations-from-file=PATH_TO_FILE | [--reservation=RESERVATION
      : --reservation-zone=RESERVATION_ZONE
      --accelerator=[count=COUNT],[type=TYPE]
      --local-ssd=[interface=INTERFACE],[size=SIZE]
      --machine-type=MACHINE_TYPE --min-cpu-platform=MIN_CPU_PLATFORM
      --require-specific-reservation --resource-policies=[KEY=VALUE,...]
      --vm-count=VM_COUNT --share-setting=SHARE_SETTING
      --share-with=SHARE_WITH,[SHARE_WITH,...]]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
COMMITMENT
   Name of the commitment to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--plan` | one of: 12-month, 36-month |  | Duration of the commitment. PLAN must be one of: 12-month, 36-month. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--auto-renew` |  |  | Enable auto renewal for the commitment. |
| `--custom-end-time` | CUSTOM_END_TIME |  | Specifies a custom future end date and extends the commitment's ongoing term. |
| `--merge-source-commitments` | MERGE_SOURCE_COMMITMENTS |  | Creates the new commitment by merging the specified source commitments and combining their resources. |
| `--region` | REGION |  | Region of the commitment to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--split-source-commitment` | SPLIT_SOURCE_COMMITMENT |  | Creates the new commitment by splitting the specified source commitment and redistributing the specified resources. |
| `--type` | one of: accelerator-optimized, accelerator-optimized-a3, accelerator-optimized-a3-mega, accelerator-optimized-a3-ultra, accelerator-optimized-a4, compute-optimized, compute-optimized-c2d, compute-optimized-c3, compute-optimized-c3d, compute-optimized-h3, compute-optimized-h4d, general-purpose, general-purpose-c4, general-purpose-c4a, general-purpose-c4d, general-purpose-e2, general-purpose-n2, general-purpose-n2d, general-purpose-n4, general-purpose-n4d, general-purpose-t2d, graphics-optimized, graphics-optimized-g4, memory-optimized, memory-optimized-m3, memory-optimized-m4, memory-optimized-m4-6tb, memory-optimized-x4-1440-24t, memory-optimized-x4-16tb, memory-optimized-x4-1920-32t, memory-optimized-x4-24tb, memory-optimized-x4-32tb, memory-optimized-x4-480-6t, memory-optimized-x4-480-8t, memory-optimized-x4-960-12t, memory-optimized-x4-960-16t, storage-optimized-z3 | general-purpose | Type of commitment. memory-optimized indicates that the commitment is for memory-optimized VMs. TYPE must be one of: accelerator-optimized, accelerator-optimized-a3, accelerator-optimized-a3-mega, accelerator-optimized-a3-ultra, accelerator-optimized-a4, compute-optimized, compute-optimized-c2d, compute-optimized-c3, compute-optimized-c3d, compute-optimized-h3, compute-optimized-h4d, general-purpose, general-purpose-c4, general-purpose-c4a, general-purpose-c4d, general-purpose-e2, general-purpose-n2, general-purpose-n2d, general-purpose-n4, general-purpose-n4d, general-purpose-t2d, graphics-optimized, graphics-optimized-g4, memory-optimized, memory-optimized-m3, memory-optimized-m4, memory-optimized-m4-6tb, memory-optimized-x4-1440-24t, memory-optimized-x4-16tb, memory-optimized-x4-1920-32t, memory-optimized-x4-24tb, memory-optimized-x4-32tb, memory-optimized-x4-480-6t, memory-optimized-x4-480-8t, memory-optimized-x4-960-12t, memory-optimized-x4-960-16t, storage-optimized-z3. |


**Examples:**
```bash
To create a commitment called commitment-1 in the us-central1 region, with
a 12-month plan, 9GB of memory and 4 vcpu cores, run:

    $ gcloud compute commitments create commitment-1 --plan=12-month \
        --resources=memory=9GB,vcpu=4 --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/commitments/create)

---
### `gcloud compute commitments create-license`

Create Compute Engine license-based commitments

Create Compute Engine license-based commitments.

**Synopsis:**
```
gcloud compute commitments create-license COMMITMENT --amount=AMOUNT
    --license=LICENSE --plan=PLAN [--cores-per-license=CORES_PER_LICENSE]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
COMMITMENT
   Name of the commitment to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--amount` | AMOUNT |  | Number of licenses purchased. |
| `--license` | LICENSE |  | Applicable license URI. For example: https://www.googleapis.com/compute/v1/projects/suse-sap-cloud/global/licenses/sles-sap-12 |
| `--plan` | one of: 12-month, 36-month |  | Duration of the commitment. PLAN must be one of: 12-month, 36-month. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cores-per-license` | CORES_PER_LICENSE |  | Core range of the instance. Must be one of: 1-2, 3-4, 5+. Required for SAP licenses. |
| `--region` | REGION |  | Region of the commitment to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To create a commitment called commitment-1 in the us-central1 region with
36-month plan, sles-sap-12 license, 1-2 cores, run:

    $ gcloud compute commitments create-license commitment-1 \
        --plan=36-month \
        --license=https://www.googleapis.com/compute/v1/projects/\
    suse-sap-cloud/global/licenses/sles-sap-12 --region=us-central1 \
        --amount=1 --cores-per-license=1-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/commitments/create-license)

---
### `gcloud compute commitments describe`

Describe a Compute Engine commitment

Describe a Compute Engine commitment.

**Synopsis:**
```
gcloud compute commitments describe COMMITMENT [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
COMMITMENT
   Name of the commitment to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the commitment to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To describe the commitment called commitment-1 in the us-central1 region,
run:

    $ gcloud compute commitments describe commitment-1 \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/commitments/describe)

---
### `gcloud compute commitments list`

List Compute Engine commitments

List Compute Engine commitments.

**Synopsis:**
```
gcloud compute commitments list [NAME ...] [--regexp=REGEXP, -r REGEXP]
    [--regions=REGION,[REGION,...]] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[NAME ...]
   (DEPRECATED) If provided, show details for the specified names and/or
   URIs of resources.

   Argument NAME is deprecated. Use --filter="name=( 'NAME' ... )"
   instead.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |
| `--regions` | REGION,[REGION,...] |  | If provided, only resources from the given regions are queried. |


**Examples:**
```bash
To list commitments, run:

    $ gcloud compute commitments list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/commitments/list)

---
### `gcloud compute commitments update`

Update Compute Engine commitments

Update Compute Engine commitments.

**Synopsis:**
```
gcloud compute commitments update COMMITMENT [--auto-renew]
    [--custom-end-time=CUSTOM_END_TIME] [--plan=PLAN] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
COMMITMENT
   Name of the commitment to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--auto-renew` |  |  | Enable auto renewal for the commitment. |
| `--custom-end-time` | CUSTOM_END_TIME |  | Specifies a custom future end date and extends the commitment's ongoing term. |
| `--plan` | PLAN |  | Duration of the commitment. PLAN must be (only one value is supported): 36-month. |
| `--region` | REGION |  | Region of the commitment to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To enable auto renewal on a commitment called commitment-1 in the
us-central1 region, run:

    $ gcloud compute commitments update commitment-1 --auto-renew \
        --region=us-central1

To disable auto renewal on a commitment called commitment-1 in the
us-central1 region, run:

    $ gcloud compute commitments update commitment-1 --no-auto-renew \
        --region=us-central1

To upgrade the term of a commitment called commitment-1 from 12-month to
36-month, in the us-central1 region, run:

    $ gcloud compute commitments update commitment-1 --plan=36-month \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/commitments/update)

---