# gcloud biglake iceberg tables

manage BigLake Iceberg REST catalog tables

### `gcloud biglake iceberg tables create`

Create a BigLake Iceberg table

Creates a BigLake Iceberg table from a JSON creation-request file specifying the table schema and metadata.

**Synopsis:**
```
gcloud biglake iceberg tables create --create-from-file=CREATE_FROM_FILE
    (--namespace=NAMESPACE : --catalog=CATALOG) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--create-from-file` | CREATE_FROM_FILE |  | Path to a JSON file containing the table creation request. The format must follow the Apache Iceberg REST Catalog Open API specification for `CreateTableRequest`. The fields `name` and `schema` must be specified. |
| `--namespace` | NAMESPACE |  | ID of the namespace or fully qualified identifier for the namespace. |
| `--catalog` | CATALOG |  | The Iceberg Catalog for the resource. |

**Examples:**
```bash
# To create a table my_table in parent catalog my-catalog and namespace
# my-namespace using a creation request from table_creation.json, run:
gcloud biglake iceberg tables create --namespace=my-namespace \
    --catalog=my-catalog --create-from-file=table_creation.json
```

The table `name` and `schema` fields are required and must be specified in `table_creation.json`. Example `table_creation.json`:

```json
{
  "name": "my_table",
  "location": "gs://my-catalog/my-namespace/my_table",
  "schema": {
    "type": "struct",
    "schema-id": 0,
    "fields": [
      {"id": 1, "name": "user_id", "required": true, "type": "long",
       "doc": "Unique identifier for the user"},
      {"id": 2, "name": "username", "required": false, "type": "string"}
    ]
  },
  "partition-spec": {
    "spec-id": 0,
    "fields": [
      {"name": "user_id_bucket", "transform": "bucket[5]",
       "source-id": 1, "partition-id": 1001}
    ]
  },
  "write-order": {
    "order-id": 0,
    "fields": [
      {"transform": "identity", "source-id": 1, "direction": "asc",
       "null-order": "nulls-last"}
    ]
  },
  "stage-create": false,
  "properties": {
    "owner": "owner",
    "environment": "test",
    "write.format.default": "parquet",
    "comment": "Creating a new table"
  }
}
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/tables/create)

---
### `gcloud biglake iceberg tables delete`

Delete a BigLake Iceberg table

**Synopsis:**
```
gcloud biglake iceberg tables delete
    (TABLE : --catalog=CATALOG --namespace=NAMESPACE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - The Iceberg Table to delete. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument TABLE on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

  --catalog=CATALOG
     The Iceberg Catalog for the resource.

  --namespace=NAMESPACE
     The Iceberg Namespace for the resource.
```

**Examples:**
```bash
# To delete table my-table in parent catalog my-catalog and namespace
# my-namespace, run:
gcloud biglake iceberg tables delete my-table --namespace=my-namespace \
    --catalog=my-catalog
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/tables/delete)

---
### `gcloud biglake iceberg tables describe`

Describe a BigLake Iceberg table

**Synopsis:**
```
gcloud biglake iceberg tables describe
    (TABLE : --catalog=CATALOG --namespace=NAMESPACE)
    [--snapshots=SNAPSHOTS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - The Iceberg Table to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument TABLE on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

  --catalog=CATALOG
     The Iceberg Catalog for the resource.

  --namespace=NAMESPACE
     The Iceberg Namespace for the resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--snapshots` | SNAPSHOTS |  | Snapshot to get. |

**Examples:**
```bash
# To describe table my-table in parent catalog my-catalog and namespace
# my-namespace, run:
gcloud biglake iceberg tables describe my-table --namespace=my-namespace \
    --catalog=my-catalog
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/tables/describe)

---
### `gcloud biglake iceberg tables get-iam-policy`

Get the IAM policy for a BigLake Iceberg REST catalog table

**Synopsis:**
```
gcloud biglake iceberg tables get-iam-policy
    (TABLE : --catalog=CATALOG --namespace=NAMESPACE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - The Iceberg Table to get the IAM policy for.

To set the project attribute:
 * provide the argument TABLE on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

  --catalog=CATALOG
     The Iceberg Catalog for the resource.

  --namespace=NAMESPACE
     The Iceberg Namespace for the resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service-determined | Maximum number of resources per page. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. Prefix a field with `~` for descending order. |

**Examples:**
```bash
# To get the IAM policy for the catalog my-catalog, namespace my-namespace,
# and table my-table run:
gcloud biglake iceberg tables get-iam-policy my-table --catalog=my-catalog \
    --namespace=my-namespace
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/tables/get-iam-policy)

---
### `gcloud biglake iceberg tables list`

List BigLake Iceberg REST tables

**Synopsis:**
```
gcloud biglake iceberg tables list (--namespace=NAMESPACE : --catalog=CATALOG)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--namespace` | NAMESPACE |  | ID of the namespace or fully qualified identifier for the namespace. |
| `--catalog` | CATALOG |  | The Iceberg Catalog for the resource. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service-determined | Maximum number of resources per page. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. Prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
# To list tables in parent catalog my-catalog and namespace my-namespace,
# run:
gcloud biglake iceberg tables list --namespace=my-namespace --catalog=my-catalog
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/tables/list)

---
### `gcloud biglake iceberg tables register`

Register a BigLake Iceberg table

**Synopsis:**
```
gcloud biglake iceberg tables register
    (TABLE : --catalog=CATALOG --namespace=NAMESPACE)
    --metadata-location=METADATA_LOCATION [--overwrite]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - The Iceberg Table to register. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument TABLE on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

  --catalog=CATALOG
     The Iceberg Catalog for the resource.

  --namespace=NAMESPACE
     The Iceberg Namespace for the resource.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--metadata-location` | METADATA_LOCATION |  | Metadata location of the table. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--overwrite` |  |  | Overwrite the table if it already exists. |

**Examples:**
```bash
# To register table my-table in parent catalog my-catalog and namespace
# my-namespace, run:
gcloud biglake iceberg tables register my-table --namespace=my-namespace \
    --catalog=my-catalog --metadata-location=gs://my-bucket/metadata.json

# To overwrite table my-table in parent catalog my-catalog and namespace
# my-namespace, run:
gcloud biglake iceberg tables register my-table --namespace=my-namespace \
    --catalog=my-catalog --metadata-location=gs://my-bucket/metadata.json \
    --overwrite
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/tables/register)

---
### `gcloud biglake iceberg tables set-iam-policy`

Set the IAM policy for a BigLake Iceberg REST catalog table

**Synopsis:**
```
gcloud biglake iceberg tables set-iam-policy
    (TABLE : --catalog=CATALOG --namespace=NAMESPACE) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - The Iceberg Table to set the IAM policy for.

To set the project attribute:
 * provide the argument TABLE on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

  --catalog=CATALOG
     The Iceberg Catalog for the resource.

  --namespace=NAMESPACE
     The Iceberg Namespace for the resource.

  POLICY_FILE
     Path to a local JSON or YAML formatted file containing a valid policy.
     The output of the get-iam-policy command is a valid file, as is any
     JSON or YAML file conforming to the structure of a Policy.
```

**Examples:**
```bash
# To set the IAM policy for the table my-table in catalog my-catalog and
# namespace my-namespace with the policy in policy.json run:
gcloud biglake iceberg tables set-iam-policy my-table policy.json \
    --catalog=my-catalog --namespace=my-namespace
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/tables/set-iam-policy)

---
### `gcloud biglake iceberg tables update`

Update a BigLake Iceberg table

**Synopsis:**
```
gcloud biglake iceberg tables update
    (TABLE : --catalog=CATALOG --namespace=NAMESPACE) [--clear-properties]
    [--remove-properties=[KEY,...]] [--update-properties=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - The Iceberg Table to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument TABLE on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

  --catalog=CATALOG
     The Iceberg Catalog for the resource.

  --namespace=NAMESPACE
     The Iceberg Namespace for the resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--clear-properties` |  |  | Clear all properties from the namespace. |
| `--remove-properties` | [KEY,...] |  | List of properties to remove. |
| `--update-properties` | [KEY=VALUE,...] |  | List of properties to update or add. |

**Examples:**
```bash
# Update or add properties on a table:
gcloud biglake iceberg tables update my-table --namespace=my-namespace \
    --catalog=my-catalog --update-properties=key1=value1,key2=value2

# Remove specific properties:
gcloud biglake iceberg tables update my-table --namespace=my-namespace \
    --catalog=my-catalog --remove-properties=key1,key2

# Clear all properties:
gcloud biglake iceberg tables update my-table --namespace=my-namespace \
    --catalog=my-catalog --clear-properties
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/tables/update)

---
