# gcloud biglake iceberg namespaces

manage BigLake Iceberg REST catalog namespaces

### `gcloud biglake iceberg namespaces create`

Create a BigLake Iceberg REST namespace

**Synopsis:**
```
gcloud biglake iceberg namespaces create (NAMESPACE : --catalog=CATALOG)
    [--properties=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The Iceberg Namespace to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument NAMESPACE on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --catalog=CATALOG
     The Iceberg Catalog for the resource.

     To set the catalog attribute:
     + provide the argument NAMESPACE on the command line with a fully
       specified name;
     + provide the argument --catalog on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--properties` | [KEY=VALUE,...] |  | Properties associated with the namespace. |

**Examples:**
```bash
# To create a namespace in parent catalog my-catalog, run:
gcloud biglake iceberg namespaces create my-namespace --catalog=my-catalog

# To create a namespace in parent catalog my-catalog, with properties
# key1=value1,key2=value2, run:
gcloud biglake iceberg namespaces create my-namespace --catalog=my-catalog \
    --properties=key1=value1,key2=value2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/namespaces/create)

---
### `gcloud biglake iceberg namespaces delete`

Delete a BigLake Iceberg REST namespace

**Synopsis:**
```
gcloud biglake iceberg namespaces delete (NAMESPACE : --catalog=CATALOG)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The Iceberg Namespace to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument NAMESPACE on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

  --catalog=CATALOG
     The Iceberg Catalog for the resource.
```

**Examples:**
```bash
# To delete a namespace in parent catalog my-catalog, run:
gcloud biglake iceberg namespaces delete my-namespace --catalog=my-catalog
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/namespaces/delete)

---
### `gcloud biglake iceberg namespaces describe`

Describe a BigLake Iceberg REST namespace

**Synopsis:**
```
gcloud biglake iceberg namespaces describe (NAMESPACE : --catalog=CATALOG)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The Iceberg Namespace to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument NAMESPACE on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

  --catalog=CATALOG
     The Iceberg Catalog for the resource.
```

**Examples:**
```bash
# To describe a namespace in parent catalog my-catalog, run:
gcloud biglake iceberg namespaces describe my-namespace --catalog=my-catalog
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/namespaces/describe)

---
### `gcloud biglake iceberg namespaces get-iam-policy`

Get the IAM policy for a BigLake Iceberg REST catalog namespace

**Synopsis:**
```
gcloud biglake iceberg namespaces get-iam-policy
    (NAMESPACE : --catalog=CATALOG) [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The Iceberg Namespace to get the IAM policy for.

To set the project attribute:
 * provide the argument NAMESPACE on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

  --catalog=CATALOG
     The Iceberg Catalog for the resource.
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
# To get the IAM policy for the catalog my-catalog and namespace
# my-namespace run:
gcloud biglake iceberg namespaces get-iam-policy my-namespace --catalog=my-catalog
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/namespaces/get-iam-policy)

---
### `gcloud biglake iceberg namespaces list`

List BigLake Iceberg REST namespaces

**Synopsis:**
```
gcloud biglake iceberg namespaces list --catalog=CATALOG
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--catalog` | CATALOG |  | ID of the catalog or fully qualified identifier for the catalog. |

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
# To list namespaces in parent catalog my-catalog, run:
gcloud biglake iceberg namespaces list --catalog=my-catalog
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/namespaces/list)

---
### `gcloud biglake iceberg namespaces set-iam-policy`

Set the IAM policy for a BigLake Iceberg REST catalog namespace

**Synopsis:**
```
gcloud biglake iceberg namespaces set-iam-policy
    (NAMESPACE : --catalog=CATALOG) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The Iceberg Namespace to set the IAM policy for.

To set the project attribute:
 * provide the argument NAMESPACE on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

  --catalog=CATALOG
     The Iceberg Catalog for the resource.

  POLICY_FILE
     Path to a local JSON or YAML formatted file containing a valid policy.
     The output of the get-iam-policy command is a valid file, as is any
     JSON or YAML file conforming to the structure of a Policy.
```

**Examples:**
```bash
# To set the IAM policy for the namespace my-namespace in catalog
# my-catalog with the policy in policy.json run:
gcloud biglake iceberg namespaces set-iam-policy my-namespace policy.json \
    --catalog=my-catalog
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/namespaces/set-iam-policy)

---
### `gcloud biglake iceberg namespaces update`

Update a BigLake Iceberg REST namespace

**Synopsis:**
```
gcloud biglake iceberg namespaces update (NAMESPACE : --catalog=CATALOG)
    [--clear-properties] [--remove-properties=[KEY,...]]
    [--update-properties=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The Iceberg Namespace to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument NAMESPACE on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

  --catalog=CATALOG
     The Iceberg Catalog for the resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--clear-properties` |  |  | Clear all properties from the namespace. |
| `--remove-properties` | [KEY,...] |  | List of properties to remove. |
| `--update-properties` | [KEY=VALUE,...] |  | List of properties to update or add. |

**Examples:**
```bash
# Update or add properties on a namespace:
gcloud biglake iceberg namespaces update my-namespace --catalog=my-catalog \
    --update-properties=key1=value1,key2=value2

# Remove specific properties:
gcloud biglake iceberg namespaces update my-namespace --catalog=my-catalog \
    --remove-properties=key1,key2

# Clear all properties:
gcloud biglake iceberg namespaces update my-namespace --catalog=my-catalog \
    --clear-properties
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/biglake/iceberg/namespaces/update)

---
