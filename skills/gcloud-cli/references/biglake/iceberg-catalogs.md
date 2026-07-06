# gcloud biglake iceberg catalogs

manage BigLake Iceberg REST catalogs

### `gcloud biglake iceberg catalogs create`

Create a BigLake Iceberg REST catalog

**Synopsis:**
```
gcloud biglake iceberg catalogs create CATALOG --catalog-type=CATALOG_TYPE
    [--credential-mode=CREDENTIAL_MODE; default="end-user"]
    [--default-location=DEFAULT_LOCATION] [--description=DESCRIPTION]
    [--primary-location=PRIMARY_LOCATION]
    [--restricted-locations=[LOCATION,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Catalog resource - The Iceberg Catalog to create. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument CATALOG on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CATALOG
     ID of the catalog or fully qualified identifier for the catalog.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--catalog-type` | CATALOG_TYPE |  | Catalog type to create the catalog with. Must be one of: `biglake` (BigLake Iceberg catalog allowing namespaces and tables to map to locations beyond the catalog's default), `gcs-bucket` (a catalog backed by a Cloud Storage bucket). |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--credential-mode` | CREDENTIAL_MODE | `end-user` | Credential mode to create the catalog with. Must be one of: `end-user` (use end user credentials to access the catalog), `vended-credentials` (use vended credentials to access the catalog). |
| `--default-location` | DEFAULT_LOCATION |  | Can only be used with BigLake catalogs. The default storage location for the catalog, e.g. `gs://my-bucket/...`. |
| `--description` | DESCRIPTION |  | Description of the resource. |
| `--primary-location` | PRIMARY_LOCATION |  | Primary location for mirroring the remote catalog metadata. It must be a BigLake-supported location, and it should be proximate to the remote catalog's location for better performance and lower cost. |
| `--restricted-locations` | [LOCATION,...] |  | Additional Google Cloud Storage buckets and locations (e.g. `gs://my-other-bucket/...`) that are permitted for use by resources within a catalog. This field is currently only used for BigLake catalogs. |

**Examples:**
```bash
# To add a catalog using a Cloud Storage bucket my-catalog-bucket, run:
gcloud biglake iceberg catalogs create my-catalog-bucket --catalog-type=gcs-bucket

# To create a catalog using a Cloud Storage bucket my-catalog-bucket with
# vended credentials, run:
gcloud biglake iceberg catalogs create my-catalog-bucket \
    --catalog-type=gcs-bucket --credential-mode=vended-credentials
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/catalogs/create)

---
### `gcloud biglake iceberg catalogs delete`

Delete a BigLake Iceberg REST catalog

**Synopsis:**
```
gcloud biglake iceberg catalogs delete CATALOG [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Catalog resource - The Iceberg Catalog to delete. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument CATALOG on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CATALOG
     ID of the catalog or fully qualified identifier for the catalog.
```

(No examples in the official reference page.)

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/catalogs/delete)

---
### `gcloud biglake iceberg catalogs describe`

Describe a BigLake Iceberg REST catalog

**Synopsis:**
```
gcloud biglake iceberg catalogs describe CATALOG [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Catalog resource - The Iceberg Catalog to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument CATALOG on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CATALOG
     ID of the catalog or fully qualified identifier for the catalog.
```

(No examples in the official reference page.)

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/catalogs/describe)

---
### `gcloud biglake iceberg catalogs failover`

Failover a BigLake Iceberg REST catalog

Failover a BigLake Iceberg REST catalog to a different primary replica region.

**Synopsis:**
```
gcloud biglake iceberg catalogs failover CATALOG
    --primary-replica=PRIMARY_REPLICA
    [--conditional-failover-replication-time=CONDITIONAL_FAILOVER_REPLICATION_TIME]
    [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Catalog resource - The Iceberg Catalog to failover. This represents a Cloud
resource.

To set the project attribute:
 * provide the argument CATALOG on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CATALOG
     ID of the catalog or fully qualified identifier for the catalog.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--primary-replica` | PRIMARY_REPLICA |  | The primary replica region to failover to. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--conditional-failover-replication-time` | CONDITIONAL_FAILOVER_REPLICATION_TIME |  | If not specified, wait for all data from the source region to replicate to the new primary region before completing the failover, with no data loss. If specified, the failover will be executed immediately, accepting data loss of any data committed after the specified timestamp. This timestamp must be in UTC format, e.g. `2025-10-09T01:13:34.038262Z`. |
| `--validate-only` |  |  | If true, the failover will be validated but not executed. |

(No examples in the official reference page.)

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/catalogs/failover)

---
### `gcloud biglake iceberg catalogs get-iam-policy`

Get the IAM policy for a BigLake Iceberg REST catalog

**Synopsis:**
```
gcloud biglake iceberg catalogs get-iam-policy CATALOG [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Catalog resource - The Iceberg Catalog to get the IAM policy for. This
represents a Cloud resource.

To set the project attribute:
 * provide the argument CATALOG on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CATALOG
     ID of the catalog or fully qualified identifier for the catalog.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. See `gcloud topic filters` for details. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service-determined | Maximum number of resources per page. The default is determined by the service if it supports paging, otherwise unlimited. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. Prefix a field with `~` for descending order. |

**Examples:**
```bash
# To get the IAM policy for the catalog my-catalog run:
gcloud biglake iceberg catalogs get-iam-policy my-catalog
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/catalogs/get-iam-policy)

---
### `gcloud biglake iceberg catalogs list`

List BigLake Iceberg REST catalogs

**Synopsis:**
```
gcloud biglake iceberg catalogs list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service-determined | Maximum number of resources per page. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. Prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. |

(No examples in the official reference page.)

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/catalogs/list)

---
### `gcloud biglake iceberg catalogs set-iam-policy`

Set the IAM policy for a BigLake Iceberg REST catalog

**Synopsis:**
```
gcloud biglake iceberg catalogs set-iam-policy CATALOG POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Catalog resource - The Iceberg Catalog to set the IAM policy for. This
represents a Cloud resource.

To set the project attribute:
 * provide the argument CATALOG on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CATALOG
     ID of the catalog or fully qualified identifier for the catalog.

  POLICY_FILE
     Path to a local JSON or YAML formatted file containing a valid policy.
     The output of the get-iam-policy command is a valid file, as is any
     JSON or YAML file conforming to the structure of a Policy.
```

**Examples:**
```bash
# To set the IAM policy for the catalog my-catalog with the policy in
# policy.json run:
gcloud biglake iceberg catalogs set-iam-policy my-catalog policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/catalogs/set-iam-policy)

---
### `gcloud biglake iceberg catalogs update`

Update a BigLake Iceberg REST catalog

**Synopsis:**
```
gcloud biglake iceberg catalogs update CATALOG
    [--catalog-type=CATALOG_TYPE]
    [--credential-mode=CREDENTIAL_MODE; default="end-user"]
    [--description=DESCRIPTION] [--restricted-locations=[LOCATION,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Catalog resource - The Iceberg Catalog to update. This represents a Cloud
resource.

To set the project attribute:
 * provide the argument CATALOG on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CATALOG
     ID of the catalog or fully qualified identifier for the catalog.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--catalog-type` | CATALOG_TYPE |  | Catalog type to update the catalog with. Currently only updating to a BigLake catalog type is supported. Must be: `biglake` (BigLake Iceberg catalog allowing namespaces and tables to map to locations beyond the catalog's default). |
| `--credential-mode` | CREDENTIAL_MODE | `end-user` | Credential mode for the catalog. Must be one of: `end-user` (use end user credentials to access the catalog), `vended-credentials` (use vended credentials to access the catalog). |
| `--description` | DESCRIPTION |  | Description of the resource. |
| `--restricted-locations` | [LOCATION,...] |  | Additional Google Cloud Storage buckets and locations permitted for use by resources within a catalog. This field is currently only used for BigLake catalogs. |

**Examples:**
```bash
# To update the description of a catalog my-catalog, run:
gcloud biglake iceberg catalogs update my-catalog --description="updated description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/catalogs/update)

---
