# gcloud oracle-database exascale-db-storage-vaults

manage Exascale Db Storage Vault resources

### `gcloud oracle-database exascale-db-storage-vaults create`

Create exascaleDbStorageVaults

Create an exascaleDbStorageVault

**Synopsis:**
```
gcloud oracle-database exascale-db-storage-vaults create
    (EXASCALE_DB_STORAGE_VAULT : --location=LOCATION)
    --display-name=DISPLAY_NAME
    (--exascale-db-storage-details-total-size-gbs=EXASCALE_DB_STORAGE_DETAILS_TOTAL_SIZE_GBS : --properties-additional-flash-cache-percent=PROPERTIES_ADDITIONAL_FLASH_CACHE_PERCENT --properties-description=PROPERTIES_DESCRIPTION)
    [--async] [--gcp-oracle-zone=GCP_ORACLE_ZONE] [--labels=[LABELS,...]]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ExascaleDbStorageVault resource - Identifier. The resource name of the
ExascaleDbStorageVault. Format:
projects/{project}/locations/{location}/exascaleDbStorageVaults/{exascale_db_storage_vault}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument exascale_db_storage_vault on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXASCALE_DB_STORAGE_VAULT
     ID of the exascaleDbStorageVault or fully qualified identifier for
     the exascaleDbStorageVault.

     To set the exascale_db_storage_vault attribute:
     + provide the argument exascale_db_storage_vault on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the exascaleDbStorageVault resource.

     To set the location attribute:
     + provide the argument exascale_db_storage_vault on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | The display name for the ExascaleDbStorageVault. The name does not have to be unique within your project. The name must be 1-255 characters long and can only contain alphanumeric characters. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--gcp-oracle-zone` | GCP_ORACLE_ZONE |  | The GCP Oracle zone where Oracle ExascaleDbStorageVault is hosted. Example: us-east4-b-r2. If not specified, the system will pick a zone based on availability. |
| `--labels` | [LABELS,...] |  | The labels or tags associated with the ExascaleDbStorageVault. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create the exascaleDbStorageVault, run:

    $ gcloud oracle-database exascale-db-storage-vaults create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/exascale-db-storage-vaults/create)

---
### `gcloud oracle-database exascale-db-storage-vaults delete`

Delete exascaleDbStorageVaults

Delete an exascaleDbStorageVault

**Synopsis:**
```
gcloud oracle-database exascale-db-storage-vaults delete
    (EXASCALE_DB_STORAGE_VAULT : --location=LOCATION) [--async]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ExascaleDbStorageVault resource - The name of the ExascaleDbStorageVault
in the following format:
projects/{project}/locations/{location}/exascaleDbStorageVaults/{exascale_db_storage_vault}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument exascale_db_storage_vault on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXASCALE_DB_STORAGE_VAULT
     ID of the exascaleDbStorageVault or fully qualified identifier for
     the exascaleDbStorageVault.

     To set the exascale_db_storage_vault attribute:
     + provide the argument exascale_db_storage_vault on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the exascaleDbStorageVault resource.

     To set the location attribute:
     + provide the argument exascale_db_storage_vault on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete the exascaleDbStorageVault, run:

    $ gcloud oracle-database exascale-db-storage-vaults delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/exascale-db-storage-vaults/delete)

---
### `gcloud oracle-database exascale-db-storage-vaults describe`

Describe exascaleDbStorageVaults

Describe an exascaleDbStorageVault

**Synopsis:**
```
gcloud oracle-database exascale-db-storage-vaults describe
    (EXASCALE_DB_STORAGE_VAULT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ExascaleDbStorageVault resource - The name of the ExascaleDbStorageVault
in the following format:
projects/{project}/locations/{location}/exascaleDbStorageVaults/{exascale_db_storage_vault}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument exascale_db_storage_vault on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXASCALE_DB_STORAGE_VAULT
     ID of the exascaleDbStorageVault or fully qualified identifier for
     the exascaleDbStorageVault.

     To set the exascale_db_storage_vault attribute:
     + provide the argument exascale_db_storage_vault on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the exascaleDbStorageVault resource.

     To set the location attribute:
     + provide the argument exascale_db_storage_vault on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the exascaleDbStorageVault, run:

    $ gcloud oracle-database exascale-db-storage-vaults describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/exascale-db-storage-vaults/describe)

---
### `gcloud oracle-database exascale-db-storage-vaults list`

List exascaleDbStorageVaults

**Synopsis:**
```
gcloud oracle-database exascale-db-storage-vaults list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all exascaleDbStorageVaults, run:

    $ gcloud oracle-database exascale-db-storage-vaults list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/exascale-db-storage-vaults/list)

---