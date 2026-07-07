# gcloud apihub external-apis

manage External Api resources

### `gcloud apihub external-apis create`

Create an External Api

Create an external api.

**Synopsis:**
```
gcloud apihub external-apis create (EXTERNAL_API : --location=LOCATION)
    --display-name=DISPLAY_NAME [--attributes=[ATTRIBUTES,...]]
    [--description=DESCRIPTION]
    [--documentation-external-uri=DOCUMENTATION_EXTERNAL_URI]
    [--endpoints=[ENDPOINTS,...]] [--paths=[PATHS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ExternalApi resource - Identifier. Format:
projects/{project}/locations/{location}/externalApi/{externalApi}. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group
but can be set in other ways.

To set the project attribute:
 * provide the argument external_api on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXTERNAL_API
     ID of the externalApi or fully qualified identifier for the
     externalApi.

     To set the external_api attribute:
     + provide the argument external_api on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the externalApi resource.

     To set the location attribute:
     + provide the argument external_api on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Display name of the external API. Max length is 63 characters (Unicode Code Points). |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attributes` | [ATTRIBUTES,...] |  | The list of user defined attributes associated with the Version resource. The key is the attribute name. It will be of the format: projects/{project}/locations/{location}/attributes/{attribute}. The value is the attribute values associated with the resource. |
| `--description` | DESCRIPTION |  | Description of the external API. Max length is 2000 characters (Unicode Code Points). |
| `--documentation-external-uri` | DOCUMENTATION_EXTERNAL_URI |  | The uri of the externally hosted documentation. |
| `--endpoints` | [ENDPOINTS,...] |  | List of endpoints on which this API is accessible. |
| `--paths` | [PATHS,...] |  | List of paths served by this API. |

**Examples:**
```bash
To create an external API with the ID `my-external-api`, run:

    $ gcloud apihub external-apis create --external-api=my-external-api \
        --display-name="My External API" --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/external-apis/create)

---
### `gcloud apihub external-apis delete`

Delete an External Api

Delete an external api.

**Synopsis:**
```
gcloud apihub external-apis delete (EXTERNAL_API : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ExternalApi resource - The name of the External API resource to delete.
Format:
projects/{project}/locations/{location}/externalApis/{externalApi} The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group
but can be set in other ways.

To set the project attribute:
 * provide the argument external_api on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXTERNAL_API
     ID of the externalApi or fully qualified identifier for the
     externalApi.

     To set the external_api attribute:
     + provide the argument external_api on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the externalApi resource.

     To set the location attribute:
     + provide the argument external_api on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete an external API with the ID `my-external-api`, run:

    $ gcloud apihub external-apis delete my-external-api \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/external-apis/delete)

---
### `gcloud apihub external-apis describe`

Describe an External Api

Describe an external api.

**Synopsis:**
```
gcloud apihub external-apis describe (EXTERNAL_API : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ExternalApi resource - The name of the External API resource to
retrieve. Format:
projects/{project}/locations/{location}/externalApis/{externalApi} The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group
but can be set in other ways.

To set the project attribute:
 * provide the argument external_api on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXTERNAL_API
     ID of the externalApi or fully qualified identifier for the
     externalApi.

     To set the external_api attribute:
     + provide the argument external_api on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the externalApi resource.

     To set the location attribute:
     + provide the argument external_api on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe an external API with the ID `my-external-api`, run:

    $ gcloud apihub external-apis describe my-external-api \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/external-apis/describe)

---
### `gcloud apihub external-apis list`

List External Apis

List external apis.

**Synopsis:**
```
gcloud apihub external-apis list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location resource - The parent, which owns this collection of External API resources. Format: projects/{project}/locations/{location} This represents a Cloud resource. (NOTE) Some attributes are not given arguments in this group but can be set in other ways. To set the project attribute: provide the argument --location on the command line with a fully specified name; provide the argument --project on the command line; set the property core/project. This must be specified. ID of the location or fully qualified identifier for the location. To set the location attribute: provide the argument --location on the command line. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. For more details and examples of filter expressions, run $ gcloud topic filters. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--page-size` | PAGE_SIZE |  | Some services group resource list output into pages. This flag specifies the maximum number of resources per page. The default is determined by the service if it supports paging, otherwise it is unlimited (no paging). Paging may be applied before or after --filter and --limit depending on the service. |
| `--sort-by` | [FIELD,...] |  | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with "~" for descending order on that field. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. If this flag is used with --format, the formatting is applied on this URI list. To display URIs alongside other keys instead, use the uri() transform. |

**Examples:**
```bash
To list all external APIs in project `my-project` and location `us-central1`,
run:

    $ gcloud apihub external-apis list --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/external-apis/list)

---
### `gcloud apihub external-apis update`

Update an External Api

Update an external api.

**Synopsis:**
```
gcloud apihub external-apis update (EXTERNAL_API : --location=LOCATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--attributes=[ATTRIBUTES,...]
      | --update-attributes=[UPDATE_ATTRIBUTES,...]
      --clear-attributes | --remove-attributes=REMOVE_ATTRIBUTES]
    [--clear-documentation
      --documentation-external-uri=DOCUMENTATION_EXTERNAL_URI]
    [--endpoints=[ENDPOINTS,...] | --add-endpoints=[ADD_ENDPOINTS,...]
      --clear-endpoints | --remove-endpoints=[REMOVE_ENDPOINTS,...]]
    [--paths=[PATHS,...] | --add-paths=[ADD_PATHS,...]
      --clear-paths | --remove-paths=[REMOVE_PATHS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ExternalApi resource - Identifier. Format:
projects/{project}/locations/{location}/externalApi/{externalApi}. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group
but can be set in other ways.

To set the project attribute:
 * provide the argument external_api on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXTERNAL_API
     ID of the externalApi or fully qualified identifier for the
     externalApi.

     To set the external_api attribute:
     + provide the argument external_api on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the externalApi resource.

     To set the location attribute:
     + provide the argument external_api on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the external API. Max length is 2000 characters (Unicode Code Points). |
| `--display-name` | DISPLAY_NAME |  | Display name of the external API. Max length is 63 characters (Unicode Code Points). |
| `--attributes` | [ATTRIBUTES,...] |  | Set attributes to new value. The list of user defined attributes associated with the Version resource. The key is the attribute name. It will be of the format: projects/{project}/locations/{location}/attributes/{attribute}. The value is the attribute values associated with the resource. |
| `--update-attributes` | [UPDATE_ATTRIBUTES,...] |  | Update attributes value or add key value pair. The list of user defined attributes associated with the Version resource. The key is the attribute name. It will be of the format: projects/{project}/locations/{location}/attributes/{attribute}. The value is the attribute values associated with the resource. |
| `--clear-attributes` |  |  | Clear attributes value and set to empty map. |
| `--remove-attributes` | REMOVE_ATTRIBUTES |  | Remove existing value from map attributes. |
| `--clear-documentation` |  |  | Set googleCloudApihubV1ExternalApi.documentation back to default value. |
| `--documentation-external-uri` | DOCUMENTATION_EXTERNAL_URI |  | The uri of the externally hosted documentation. |
| `--endpoints` | [ENDPOINTS,...] |  | Set endpoints to new value. |
| `--add-endpoints` | [ADD_ENDPOINTS,...] |  | Add new value to endpoints list. |
| `--clear-endpoints` |  |  | Clear endpoints value and set to empty list. |
| `--remove-endpoints` | [REMOVE_ENDPOINTS,...] |  | Remove existing value from endpoints list. |
| `--paths` | [PATHS,...] |  | Set paths to new value. |
| `--add-paths` | [ADD_PATHS,...] |  | Add new value to paths list. |
| `--clear-paths` |  |  | Clear paths value and set to empty list. |
| `--remove-paths` | [REMOVE_PATHS,...] |  | Remove existing value from paths list. |

**Examples:**
```bash
To update the display name of an external API with the ID `my-external-api`,
run:

    $ gcloud apihub external-apis update my-external-api \
        --display-name="New External API Name" --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/external-apis/update)

---
