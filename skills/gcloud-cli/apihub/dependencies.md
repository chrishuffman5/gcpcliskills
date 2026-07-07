# gcloud apihub dependencies

manage Dependency resources

### `gcloud apihub dependencies create`

Create a Dependency

Create a dependency.

Note: The positional argument for Dependency ID is currently not supported. Please use the `--dependency` flag to specify the Dependency ID.

**Synopsis:**
```
gcloud apihub dependencies create (DEPENDENCY : --location=LOCATION)
    (--consumer-external-api-resource-name=CONSUMER_EXTERNAL_API_RESOURCE_NAME
      | --consumer-operation-resource-name=CONSUMER_OPERATION_RESOURCE_NAME)
    (--supplier-external-api-resource-name=SUPPLIER_EXTERNAL_API_RESOURCE_NAME
      | --supplier-operation-resource-name=SUPPLIER_OPERATION_RESOURCE_NAME)
    [--attributes=[ATTRIBUTES,...]] [--description=DESCRIPTION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dependency resource - Identifier. The name of the dependency in the API Hub.

Format: projects/{project}/locations/{location}/dependencies/{dependency}

The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but can
be set in other ways.

To set the project attribute:
 * provide the argument dependency on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPENDENCY
     ID of the dependency or fully qualified identifier for the dependency.

     To set the dependency attribute:
     + provide the argument dependency on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the dependency resource.

     To set the location attribute:
     + provide the argument dependency on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--consumer-external-api-resource-name` | CONSUMER_EXTERNAL_API_RESOURCE_NAME |  | The resource name of an external API in the API Hub. Format: `projects/{project}/locations/{location}/externalApis/{external_api}`. Part of the consumer group (reference to an entity participating in a dependency; the consumer group must be specified, and at most one of the two consumer identifier flags can be specified). |
| `--consumer-operation-resource-name` | CONSUMER_OPERATION_RESOURCE_NAME |  | The resource name of an operation in the API Hub. Format: `projects/{project}/locations/{location}/apis/{api}/versions/{version}/operations/{operation}`. Part of the consumer group (at most one of the two consumer identifier flags can be specified). |
| `--supplier-external-api-resource-name` | SUPPLIER_EXTERNAL_API_RESOURCE_NAME |  | The resource name of an external API in the API Hub. Format: `projects/{project}/locations/{location}/externalApis/{external_api}`. Part of the supplier group (reference to an entity participating in a dependency; the supplier group must be specified, and at most one of the two supplier identifier flags can be specified). |
| `--supplier-operation-resource-name` | SUPPLIER_OPERATION_RESOURCE_NAME |  | The resource name of an operation in the API Hub. Format: `projects/{project}/locations/{location}/apis/{api}/versions/{version}/operations/{operation}`. Part of the supplier group (at most one of the two supplier identifier flags can be specified). |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attributes` | [ATTRIBUTES,...] |  | The list of user defined attributes associated with the dependency resource. The key is the attribute name. It will be of the format: `projects/{project}/locations/{location}/attributes/{attribute}`. The value is the attribute values associated with the resource. Value sub-fields: `enumValues.values` (attribute values in case data type is enum; each value has `description` — the detailed description of the allowed value; `displayName` — the display name of the allowed value; `id` — the ID of the allowed value: if provided, the same will be used and the service will throw an error if the specified id is already used by another allowed value in the same attribute resource; if not provided, a system generated id derived from the display name will be used with a system generated suffix in case of duplicates; this value should be 4-63 characters and valid characters are /[a-z][0-9]-/; `immutable` — when set to true, the allowed value cannot be updated or deleted by the user, and can only be true for System defined attributes); `jsonValues.values` (data type JSON); `stringValues.values` (data type string); `uriValues.values` (data type URL, URI or IP, like gs://bucket-name/object-name). Shorthand example: `--attributes=string={enumValues={values=[{description=string,displayName=string,id=string,immutable=boolean}]},jsonValues={values=[string]},stringValues={values=[string]},uriValues={values=[string]}}`. Also accepts a JSON value or a file: `--attributes=path_to_file.(yaml\|json)`. |
| `--description` | DESCRIPTION |  | Human readable description corresponding of the dependency. |

**Examples:**
```bash
To create a dependency with the ID my-dependency, run:

    $ gcloud apihub dependencies create --dependency=my-dependency \
        --consumer=projects/my-project/locations/us-central1/apis/my-api/versions/v1/operations/get-users \
        --supplier=projects/my-project/locations/us-central1/apis/other-api/versions/v1/operations/list-items \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/dependencies/create)

---
### `gcloud apihub dependencies delete`

Delete a Dependency

Delete a dependency.

**Synopsis:**
```
gcloud apihub dependencies delete (DEPENDENCY : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dependency resource - The name of the dependency resource to delete. Format:
projects/{project}/locations/{location}/dependencies/{dependency}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but can
be set in other ways.

To set the project attribute:
 * provide the argument dependency on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPENDENCY
     ID of the dependency or fully qualified identifier for the dependency.

     To set the dependency attribute:
     + provide the argument dependency on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the dependency resource.

     To set the location attribute:
     + provide the argument dependency on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete a dependency with the ID my-dependency, run:

    $ gcloud apihub dependencies delete my-dependency \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/dependencies/delete)

---
### `gcloud apihub dependencies describe`

Describe a Dependency

Describe a dependency.

**Synopsis:**
```
gcloud apihub dependencies describe (DEPENDENCY : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dependency resource - The name of the dependency resource to retrieve. Format:
projects/{project}/locations/{location}/dependencies/{dependency}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but can
be set in other ways.

To set the project attribute:
 * provide the argument dependency on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPENDENCY
     ID of the dependency or fully qualified identifier for the dependency.

     To set the dependency attribute:
     + provide the argument dependency on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the dependency resource.

     To set the location attribute:
     + provide the argument dependency on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a dependency with the ID my-dependency, run:

    $ gcloud apihub dependencies describe my-dependency \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/dependencies/describe)

---
### `gcloud apihub dependencies list`

List Dependencies

List dependencies.

**Synopsis:**
```
gcloud apihub dependencies list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | ID of the location or fully qualified identifier for the location. Location resource - the parent which owns this collection of dependency resources. Format: `projects/{project}/locations/{location}`. This represents a Cloud resource. To set the project attribute: provide the argument `--location` on the command line with a fully specified name; provide the argument `--project` on the command line; or set the property `core/project`. To set the location attribute: provide the argument `--location` on the command line. This must be specified. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. For more details and examples of filter expressions, run `$ gcloud topic filters`. This flag interacts with other flags that are applied in this order: `--flatten`, `--sort-by`, `--filter`, `--limit`. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. This flag interacts with other flags that are applied in this order: `--flatten`, `--sort-by`, `--filter`, `--limit`. |
| `--page-size` | PAGE_SIZE | determined by service | Some services group resource list output into pages. This flag specifies the maximum number of resources per page. The default is determined by the service if it supports paging, otherwise it is unlimited (no paging). Paging may be applied before or after `--filter` and `--limit` depending on the service. |
| `--sort-by` | [FIELD,...] |  | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with `~` for descending order on that field. This flag interacts with other flags that are applied in this order: `--flatten`, `--sort-by`, `--filter`, `--limit`. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. If this flag is used with `--format`, the formatting is applied on this URI list. To display URIs alongside other keys instead, use the `uri()` transform. |

**Examples:**
```bash
To list all dependencies in project my-project and location us-central1, run:

    $ gcloud apihub dependencies list --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/dependencies/list)

---
### `gcloud apihub dependencies update`

Update a Dependency

Update a dependency.

**Synopsis:**
```
gcloud apihub dependencies update (DEPENDENCY : --location=LOCATION)
    [--description=DESCRIPTION]
    [--attributes=[ATTRIBUTES,...]
      | --update-attributes=[UPDATE_ATTRIBUTES,...] --clear-attributes
      | --remove-attributes=REMOVE_ATTRIBUTES]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dependency resource - Identifier. The name of the dependency in the API Hub.

Format: projects/{project}/locations/{location}/dependencies/{dependency}

The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but can
be set in other ways.

To set the project attribute:
 * provide the argument dependency on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPENDENCY
     ID of the dependency or fully qualified identifier for the dependency.

     To set the dependency attribute:
     + provide the argument dependency on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the dependency resource.

     To set the location attribute:
     + provide the argument dependency on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Human readable description corresponding of the dependency. |
| `--attributes` | [ATTRIBUTES,...] |  | Set attributes to new value. The list of user defined attributes associated with the dependency resource. The key is the attribute name. It will be of the format: `projects/{project}/locations/{location}/attributes/{attribute}`. The value is the attribute values associated with the resource. Value sub-fields: `enumValues.values` (attribute values in case data type is enum; each value has `description`, `displayName`, `id` — 4-63 characters, valid characters /[a-z][0-9]-/, system generated from display name if not provided; and `immutable` — when true, the allowed value cannot be updated or deleted by the user and can only be true for System defined attributes); `jsonValues.values` (data type JSON); `stringValues.values` (data type string); `uriValues.values` (data type URL, URI or IP, like gs://bucket-name/object-name). Shorthand example: `--attributes=string={enumValues={values=[{description=string,displayName=string,id=string,immutable=boolean}]},jsonValues={values=[string]},stringValues={values=[string]},uriValues={values=[string]}}`. Also accepts a JSON value or a file: `--attributes=path_to_file.(yaml\|json)`. Part of the "Update attributes" group: at most one of `--attributes` or the update/clear/remove combination can be specified. |
| `--update-attributes` | [UPDATE_ATTRIBUTES,...] |  | Update attributes value or add key value pair. The list of user defined attributes associated with the dependency resource. The key is the attribute name, of the format `projects/{project}/locations/{location}/attributes/{attribute}`; the value is the attribute values associated with the resource (same sub-field structure and shorthand as `--attributes`). Cannot be combined with `--attributes`. |
| `--clear-attributes` |  |  | Clear attributes value and set to empty map. At most one of `--clear-attributes` or `--remove-attributes` can be specified. Cannot be combined with `--attributes`. |
| `--remove-attributes` | REMOVE_ATTRIBUTES |  | Remove existing value from map attributes. Sets remove_attributes value. Shorthand example: `--remove-attributes=string,string`; JSON example: `--remove-attributes=["string"]`; file example: `--remove-attributes=path_to_file.(yaml\|json)`. At most one of `--clear-attributes` or `--remove-attributes` can be specified. Cannot be combined with `--attributes`. |

**Examples:**
```bash
To update the description of a dependency with the ID my-dependency, run:

    $ gcloud apihub dependencies update my-dependency \
        --description="New Description" --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/dependencies/update)

---
