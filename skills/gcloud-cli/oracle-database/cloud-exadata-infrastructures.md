# gcloud oracle-database cloud-exadata-infrastructures

manage Cloud Exadata Infrastructure resources

### `gcloud oracle-database cloud-exadata-infrastructures create`

Create a new ExadataInfrastructure

Creates a new ExadataInfrastructure.

**Synopsis:**
```
gcloud oracle-database cloud-exadata-infrastructures create
    (CLOUD_EXADATA_INFRASTRUCTURE : --location=LOCATION) [--async]
    [--display-name=DISPLAY_NAME] [--gcp-oracle-zone=GCP_ORACLE_ZONE]
    [--labels=[LABELS,...]] [--request-id=REQUEST_ID]
    [[--properties-shape=PROPERTIES_SHAPE
      : --properties-compute-count=PROPERTIES_COMPUTE_COUNT
      --properties-customer-contacts=[email=EMAIL]
      --properties-storage-count=PROPERTIES_STORAGE_COUNT
      --properties-total-storage-size-gb=PROPERTIES_TOTAL_STORAGE_SIZE_GB
      --maintenance-window-custom-action-timeout-mins=MAINTENANCE_WINDOW_CUSTOM_ACTION_TIMEOUT_MINS --maintenance-window-days-of-week=[MAINTENANCE_WINDOW_DAYS_OF_WEEK,
      ...]
      --maintenance-window-hours-of-day=[MAINTENANCE_WINDOW_HOURS_OF_DAY,
      ...] --maintenance-window-is-custom-action-timeout-enabled
      --maintenance-window-lead-time-week=MAINTENANCE_WINDOW_LEAD_TIME_WEEK
      --maintenance-window-months=[MAINTENANCE_WINDOW_MONTHS,...]
      --maintenance-window-patching-mode=MAINTENANCE_WINDOW_PATCHING_MODE
      --maintenance-window-preference=MAINTENANCE_WINDOW_PREFERENCE
      --maintenance-window-weeks-of-month=[MAINTENANCE_WINDOW_WEEKS_OF_MONTH,
      ...]]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CloudExadataInfrastructure resource - Identifier. The name of the Exadata
Infrastructure resource with the format:
projects/{project}/locations/{region}/cloudExadataInfrastructures/{cloud_exadata_infrastructure}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument cloud_exadata_infrastructure on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLOUD_EXADATA_INFRASTRUCTURE
     ID of the cloudExadataInfrastructure or fully qualified identifier
     for the cloudExadataInfrastructure.

     To set the cloud_exadata_infrastructure attribute:
     + provide the argument cloud_exadata_infrastructure on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the cloudExadataInfrastructure resource.

     To set the location attribute:
     + provide the argument cloud_exadata_infrastructure on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | User friendly name for this resource. |
| `--gcp-oracle-zone` | GCP_ORACLE_ZONE |  | The GCP Oracle zone where Oracle Exadata Infrastructure is hosted. Example: us-east4-b-r2. If not specified, the system will pick a zone based on availability. |
| `--labels` | [LABELS,...] |  | Labels or tags associated with the resource. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
Choose an available system shapes in your location by running gcloud
oracle-database db-system-shapes list --location=us-east4. To create
Exadata Infrastructure instance with id my-instance in the location
us-east4 with display-name my instance, compute count 2 and choosen shape
"Exadata.FOO", run:

    $ gcloud oracle-database cloud-exadata-infrastructures create \
        my-instance --location=us-east4 --display-name="my instance" \
        --properties-shape=Exadata.FOO --properties-compute-count=2 \
        --properties-storage-count=3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/cloud-exadata-infrastructures/create)

---
### `gcloud oracle-database cloud-exadata-infrastructures delete`

Delete an ExadataInfrastructure

Delete an ExadataInfrastructure.

**Synopsis:**
```
gcloud oracle-database cloud-exadata-infrastructures delete
    (CLOUD_EXADATA_INFRASTRUCTURE : --location=LOCATION) [--async]
    [--force] [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CloudExadataInfrastructure resource - The name of the Cloud Exadata
Infrastructure in the following format:
projects/{project}/locations/{location}/cloudExadataInfrastructures/{cloud_exadata_infrastructure}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument cloud_exadata_infrastructure on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLOUD_EXADATA_INFRASTRUCTURE
     ID of the cloudExadataInfrastructure or fully qualified identifier
     for the cloudExadataInfrastructure.

     To set the cloud_exadata_infrastructure attribute:
     + provide the argument cloud_exadata_infrastructure on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the cloudExadataInfrastructure resource.

     To set the location attribute:
     + provide the argument cloud_exadata_infrastructure on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | If set to true, all VM clusters for this Exadata Infrastructure will be deleted. An Exadata Infrastructure can only be deleted once all its VM clusters have been deleted. |
| `--request-id` | REQUEST_ID |  | An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete a ExadataInfrastructure with id my-instance in the location
us-east4, run:

    $ gcloud oracle-database cloud-exadata-infrastructures delete \
        my-instance --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/cloud-exadata-infrastructures/delete)

---
### `gcloud oracle-database cloud-exadata-infrastructures describe`

Get details of a ExadataInfrastructure

Get details of a ExadataInfrastructure.

**Synopsis:**
```
gcloud oracle-database cloud-exadata-infrastructures describe
    (CLOUD_EXADATA_INFRASTRUCTURE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CloudExadataInfrastructure resource - The name of the Cloud Exadata
Infrastructure in the following format:
projects/{project}/locations/{location}/cloudExadataInfrastructures/{cloud_exadata_infrastructure}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument cloud_exadata_infrastructure on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLOUD_EXADATA_INFRASTRUCTURE
     ID of the cloudExadataInfrastructure or fully qualified identifier
     for the cloudExadataInfrastructure.

     To set the cloud_exadata_infrastructure attribute:
     + provide the argument cloud_exadata_infrastructure on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the cloudExadataInfrastructure resource.

     To set the location attribute:
     + provide the argument cloud_exadata_infrastructure on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get a ExadataInfrastructure with id my-instance in the location
us-east4, run:

    $ gcloud oracle-database cloud-exadata-infrastructures describe \
        my-instance --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/cloud-exadata-infrastructures/describe)

---
### `gcloud oracle-database cloud-exadata-infrastructures list`

List all ExadataInfrastructures

List all ExadataInfrastructures.

**Synopsis:**
```
gcloud oracle-database cloud-exadata-infrastructures list
    --location=LOCATION [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all ExadataInfrastructures in the location us-east4, run:

    $ gcloud oracle-database cloud-exadata-infrastructures list \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/cloud-exadata-infrastructures/list)

---

## `gcloud oracle-database cloud-exadata-infrastructures db-servers` — manage Db Server resources
### `gcloud oracle-database cloud-exadata-infrastructures db-servers list`

List all DbServers

List all DbServers.

**Synopsis:**
```
gcloud oracle-database cloud-exadata-infrastructures db-servers list
    (--cloud-exadata-infrastructure=CLOUD_EXADATA_INFRASTRUCTURE
      : --location=LOCATION) [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cloud-exadata-infrastructure` | CLOUD_EXADATA_INFRASTRUCTURE |  | _[This must be specified.]_ ID of the cloudExadataInfrastructure or fully qualified identifier for the cloudExadataInfrastructure. To set the cloud-exadata-infrastructure attribute: + provide the argument --cloud-exadata-infrastructure on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the cloudExadataInfrastructure resource. To set the location attribute: + provide the argument --cloud-exadata-infrastructure on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all DbServers in the location us-east4, run:

    $ gcloud oracle-database cloud-exadata-infrastructures db-servers \
        list --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/cloud-exadata-infrastructures/db-servers/list)

---