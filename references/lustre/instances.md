# gcloud lustre instances

manage Instance resources

### `gcloud lustre instances create`

Creates a Managed Lustre instance

Creates a Managed Lustre instance.

**Synopsis:**
```
gcloud lustre instances create (INSTANCE : --location=LOCATION)
    --capacity-gib=CAPACITY_GIB --filesystem=FILESYSTEM --network=NETWORK
    --per-unit-storage-throughput=PER_UNIT_STORAGE_THROUGHPUT [--async]
    [--description=DESCRIPTION] [--gke-support-enabled] [--kms-key=KMS_KEY]
    [--labels=[LABELS,...]] [--placement-policy=PLACEMENT_POLICY]
    [--request-id=REQUEST_ID]
    [[--default-squash-mode=DEFAULT_SQUASH_MODE
      : --access-rules=[ipAddressRanges=IPADDRESSRANGES],
      [name=NAME],[squashMode=SQUASHMODE]
      --default-squash-gid=DEFAULT_SQUASH_GID
      --default-squash-uid=DEFAULT_SQUASH_UID]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Identifier. The name of the instance. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--capacity-gib` | CAPACITY_GIB |  | The storage capacity of the instance in gibibytes (GiB). Allowed values are from 18000 to 7632000, depending on the perUnitStorageThroughput. See Performance tiers and maximum storage capacities (https://cloud.google.com/managed-lustre/docs/create-instance#performance-tiers) for specific minimums, maximums, and step sizes for each performance tier. |
| `--filesystem` | FILESYSTEM |  | The filesystem name for this instance. This name is used by client-side tools, including when mounting the instance. Must be eight characters or less and can only contain letters and numbers. |
| `--per-unit-storage-throughput` | PER_UNIT_STORAGE_THROUGHPUT |  | _[+ provide the argument --network on the command line.]_ The throughput of the instance in MBps per TiB. Valid values are 125, 250, 500, 1000. See Performance tiers and maximum storage capacities (https://cloud.google.com/managed-lustre/docs/create-instance#performance-tiers) for more information. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A user-readable description of the instance. |
| `--gke-support-enabled` |  |  | Indicates whether you want to enable support for GKE clients. By default, GKE clients are not supported. Deprecated. No longer required for GKE instance creation. |
| `--kms-key` | KMS_KEY |  | The Cloud KMS key name to use for data encryption. If not set, the instance will use Google-managed encryption keys. If set, the instance will use customer-managed encryption keys. The key must be in the same region as the instance. The key format is: projects/{project}/locations/{location}/keyRings/{key_ring}/cryptoKeys/{key} |
| `--labels` | [LABELS,...] |  | Labels as key value pairs. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--placement-policy` | PLACEMENT_POLICY |  | The placement policy name for the instance in the format of projects/{project}/locations/{location}/resourcePolicies/{resource_policy} |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create an instance my-instance in location us-central1-a with 18000 Gib
capacity run:

    $ gcloud lustre instances create my-instance --capacity-gib=18000 \
        --location=us-central1-a \
        --network=projects/my-project/global/networks/default \
        --filesystem=lustrefs --per-unit-storage-throughput=1000
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/lustre/instances/create)

---
### `gcloud lustre instances delete`

Deletes a Managed Lustre instance

Deletes a Managed Lustre instance.

**Synopsis:**
```
gcloud lustre instances delete (INSTANCE : --location=LOCATION) [--async]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The resource name of the instance to delete, in the
format projects/{projectId}/locations/{location}/instances/{instanceId}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
to delete an instance my-instance run:

    $ gcloud lustre instances delete my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/lustre/instances/delete)

---
### `gcloud lustre instances describe`

Gets details of a single Managed Lustre instance

Gets details of a single Managed Lustre instance.

**Synopsis:**
```
gcloud lustre instances describe (INSTANCE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance resource name, in the format
projects/{projectId}/locations/{location}/instances/{instanceId}. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get the details of a single instance my-instance in location
us-central1-a run:

    $ gcloud lustre instances describe my-instance \
        --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/lustre/instances/describe)

---
### `gcloud lustre instances export-data`

Exports data from Managed Lustre instance to Cloud Storage

Exports data from Managed Lustre instance to Cloud Storage.

**Synopsis:**
```
gcloud lustre instances export-data (INSTANCE : --location=LOCATION)
    --gcs-path-uri=GCS_PATH_URI [--async] [--lustre-path=LUSTRE_PATH]
    [--request-id=REQUEST_ID] [--service-account=SERVICE_ACCOUNT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The name of the Managed Lustre instance in the format
projects/{project}/locations/{location}/instances/{instance}. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-path-uri` | GCS_PATH_URI |  | The URI to a Cloud Storage bucket, or a path within a bucket, using the format gs://<bucket_name>/<optional_path_inside_bucket>/. If a path inside the bucket is specified, it must end with a forward slash (/). |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--lustre-path` | LUSTRE_PATH |  | The root directory path to the Managed Lustre file system. Must start with /. Default is /. If you're importing data into Managed Lustre, any path other than the default must already exist on the file system. |
| `--request-id` | REQUEST_ID |  | UUID to identify requests. |


**Examples:**
```bash
To export data from my-instance to gs://my-bucket storage run:

    $ gcloud lustre instances export-data my-instance \
        --location=us-central-a --gcs-path-uri=gs://my-bucket \
        --lustre-path='/path/to/lustre/dir'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/lustre/instances/export-data)

---
### `gcloud lustre instances import-data`

Imports data from Cloud Storage to Managed Lustre instance

Imports data from Cloud Storage to Managed Lustre instance.

**Synopsis:**
```
gcloud lustre instances import-data (INSTANCE : --location=LOCATION)
    --gcs-path-uri=GCS_PATH_URI [--async] [--lustre-path=LUSTRE_PATH]
    [--request-id=REQUEST_ID] [--service-account=SERVICE_ACCOUNT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The name of the Managed Lustre instance in the format
projects/{project}/locations/{location}/instances/{instance}. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-path-uri` | GCS_PATH_URI |  | The URI to a Cloud Storage bucket, or a path within a bucket, using the format gs://<bucket_name>/<optional_path_inside_bucket>/. If a path inside the bucket is specified, it must end with a forward slash (/). |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--lustre-path` | LUSTRE_PATH |  | The root directory path to the Managed Lustre file system. Must start with /. Default is /. If you're importing data into Managed Lustre, any path other than the default must already exist on the file system. |
| `--request-id` | REQUEST_ID |  | UUID to identify requests. |


**Examples:**
```bash
To import data from gs://my-bucket storage to my-instance run:

    $ gcloud lustre instances import-data my-instance \
        --location=us-central-a --gcs-path-uri=gs://my_bucket \
        --lustre-path='/path/to/lustre/dir'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/lustre/instances/import-data)

---
### `gcloud lustre instances list`

List Lustre instances

List Managed Lustre instances.

**Synopsis:**
```
gcloud lustre instances list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all instances in particular location us-central1-a run:

    $ gcloud lustre instances list --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/lustre/instances/list)

---
### `gcloud lustre instances update`

Updates the parameters of a single Managed Lustre instance

Updates the parameters of a single Managed Lustre instance.

**Synopsis:**
```
gcloud lustre instances update (INSTANCE : --location=LOCATION) [--async]
    [--capacity-gib=CAPACITY_GIB] [--description=DESCRIPTION]
    [--[no-]gke-support-enabled]
    [--per-unit-storage-throughput=PER_UNIT_STORAGE_THROUGHPUT]
    [--placement-policy=PLACEMENT_POLICY] [--request-id=REQUEST_ID]
    [--clear- --default-squash-gid=DEFAULT_SQUASH_GID
      --default-squash-mode=DEFAULT_SQUASH_MODE
      --default-squash-uid=DEFAULT_SQUASH_UID
      --access-rules=[ipAddressRanges=IPADDRESSRANGES],
      [name=NAME],[squashMode=SQUASHMODE]
      | --add-access-rules=[ipAddressRanges=IPADDRESSRANGES],
      [name=NAME],[squashMode=SQUASHMODE] --clear-access-rules
      | --remove-access-rules=[ipAddressRanges=IPADDRESSRANGES],
      [name=NAME],[squashMode=SQUASHMODE]]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Identifier. The name of the instance. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the instance resource.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--capacity-gib` | CAPACITY_GIB |  | The storage capacity of the instance in gibibytes (GiB). Allowed values are from 18000 to 7632000, depending on the perUnitStorageThroughput. See Performance tiers and maximum storage capacities (https://cloud.google.com/managed-lustre/docs/create-instance#performance-tiers) for specific minimums, maximums, and step sizes for each performance tier. |
| `--description` | DESCRIPTION |  | A user-readable description of the instance. |
| `--[no-]gke-support-enabled` |  |  | Indicates whether you want to enable support for GKE clients. By default, GKE clients are not supported. Deprecated. No longer required for GKE instance creation. Use --gke-support-enabled to enable and --no-gke-support-enabled to disable. |
| `--per-unit-storage-throughput` | PER_UNIT_STORAGE_THROUGHPUT |  | The throughput of the instance in MBps per TiB. Valid values are 125, 250, 500, 1000. See Performance tiers and maximum storage capacities (https://cloud.google.com/managed-lustre/docs/create-instance#performance-tiers) for more information. |
| `--placement-policy` | PLACEMENT_POLICY |  | The placement policy name for the instance in the format of projects/{project}/locations/{location}/resourcePolicies/{resource_policy} |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To update the description of an instance my-instance in location
us-central1-a run:

    $ gcloud lustre instances update my-instance \
        --location=us-central1-a --description="<updated description>"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/lustre/instances/update)

---