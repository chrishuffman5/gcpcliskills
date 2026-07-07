# gcloud apihub deployments

manage Deployment resources

### `gcloud apihub deployments create`

Create a Deployment

Create a deployment.

**Synopsis:**
```
gcloud apihub deployments create (DEPLOYMENT : --location=LOCATION)
    --display-name=DISPLAY_NAME --endpoints=[ENDPOINTS,...]
    --resource-uri=RESOURCE_URI
    (--deployment-type-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --deployment-type-json-values=[DEPLOYMENT_TYPE_JSON_VALUES,...]
      | --deployment-type-string-values=[DEPLOYMENT_TYPE_STRING_VALUES,...]
      | --deployment-type-uri-values=[DEPLOYMENT_TYPE_URI_VALUES,...])
    [--attributes=[ATTRIBUTES,...]] [--description=DESCRIPTION]
    [--documentation-external-uri=DOCUMENTATION_EXTERNAL_URI]
    [--source-environment=SOURCE_ENVIRONMENT]
    [--source-project=SOURCE_PROJECT]
    [--environment-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --environment-json-values=[ENVIRONMENT_JSON_VALUES,...]
      | --environment-string-values=[ENVIRONMENT_STRING_VALUES,...]
      | --environment-uri-values=[ENVIRONMENT_URI_VALUES,...]]
    [--management-url-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --management-url-json-values=[MANAGEMENT_URL_JSON_VALUES,...]
      | --management-url-string-values=[MANAGEMENT_URL_STRING_VALUES,...]
      | --management-url-uri-values=[MANAGEMENT_URL_URI_VALUES,...]]
    [--slo-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --slo-json-values=[SLO_JSON_VALUES,...]
      | --slo-string-values=[SLO_STRING_VALUES,...]
      | --slo-uri-values=[SLO_URI_VALUES,...]]
    [--source-uri-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --source-uri-json-values=[SOURCE_URI_JSON_VALUES,...]
      | --source-uri-string-values=[SOURCE_URI_STRING_VALUES,...]
      | --source-uri-values=[SOURCE_URI_VALUES,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - Identifier. The name of the deployment.

Format: projects/{project}/locations/{location}/deployments/{deployment}

The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but can
be set in other ways.

To set the project attribute:
 * provide the argument deployment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the deployment.

     To set the deployment attribute:
     + provide the argument deployment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the deployment resource.

     To set the location attribute:
     + provide the argument deployment on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | The display name of the deployment. |
| `--endpoints` | [ENDPOINTS,...] |  | The endpoints at which this deployment resource is listening for API requests. This could be a list of complete URIs, hostnames or an IP addresses. |
| `--resource-uri` | RESOURCE_URI |  | The resource URI identifies the deployment within its gateway. For Apigee gateways, its recommended to use the format: organizations/{org}/environments/{env}/apis/{api}. For ex: if a proxy with name orders is deployed in staging environment of cymbal organization, the resource URI would be: organizations/cymbal/environments/staging/apis/orders. |
| `--deployment-type-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Required, The attribute values in case attribute data type is enum. Keys: `description` — the detailed description of the allowed value; `displayName` — the display name of the allowed value; `id` — the ID of the allowed value: if provided, the same will be used and the service will throw an error if the specified id is already used by another allowed value in the same attribute resource; if not provided, a system generated id derived from the display name will be used, with a system generated suffix in case of duplicates; this value should be 4-63 characters, and valid characters are /[a-z][0-9]-/; `immutable` — when set to true, the allowed value cannot be updated or deleted by the user; it can only be true for System defined attributes. Shorthand example: `--deployment-type-enum-values=description=string,displayName=string,id=string,immutable=boolean`; JSON example: `--deployment-type-enum-values='[{"description": "string", "displayName": "string", "id": "string", "immutable": boolean}]'`; file example: `--deployment-type-enum-values=path_to_file.(yaml\|json)`. Part of the deployment type attribute-value group: the group must be specified, and at most one of the four `--deployment-type-*` flags can be specified. |
| `--deployment-type-json-values` | [DEPLOYMENT_TYPE_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--deployment-type-*` flags can be specified. |
| `--deployment-type-string-values` | [DEPLOYMENT_TYPE_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--deployment-type-*` flags can be specified. |
| `--deployment-type-uri-values` | [DEPLOYMENT_TYPE_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--deployment-type-*` flags can be specified. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attributes` | [ATTRIBUTES,...] |  | The list of user defined attributes associated with the deployment resource. The key is the attribute name. It will be of the format: `projects/{project}/locations/{location}/attributes/{attribute}`. The value is the attribute values associated with the resource. Value sub-fields: `enumValues.values` (attribute values in case data type is enum; each value has `description` — the detailed description of the allowed value; `displayName` — the display name of the allowed value; `id` — the ID of the allowed value, 4-63 characters, valid characters /[a-z][0-9]-/, system generated from the display name if not provided; `immutable` — when true, the allowed value cannot be updated or deleted by the user and can only be true for System defined attributes); `jsonValues.values` (data type JSON); `stringValues.values` (data type string); `uriValues.values` (data type URL, URI or IP, like gs://bucket-name/object-name). Shorthand example: `--attributes=string={enumValues={values=[{description=string,displayName=string,id=string,immutable=boolean}]},jsonValues={values=[string]},stringValues={values=[string]},uriValues={values=[string]}}`. Also accepts a JSON value or a file: `--attributes=path_to_file.(yaml\|json)`. |
| `--description` | DESCRIPTION |  | The description of the deployment. |
| `--documentation-external-uri` | DOCUMENTATION_EXTERNAL_URI |  | The uri of the externally hosted documentation. (Documentation details.) |
| `--source-environment` | SOURCE_ENVIRONMENT |  | The environment at source for the deployment. For example: prod, dev, staging, etc. |
| `--source-project` | SOURCE_PROJECT |  | The project to which the deployment belongs. For Google Cloud gateways, this will refer to the project identifier. For others like Edge/OPDK, this will refer to the org identifier. |
| `--environment-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Required, The attribute values in case attribute data type is enum. Same `description`/`displayName`/`id`/`immutable` key semantics as `--deployment-type-enum-values`. Shorthand example: `--environment-enum-values=description=string,displayName=string,id=string,immutable=boolean`; also accepts JSON or `path_to_file.(yaml\|json)`. At most one of the four `--environment-*` flags can be specified. |
| `--environment-json-values` | [ENVIRONMENT_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--environment-*` flags can be specified. |
| `--environment-string-values` | [ENVIRONMENT_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--environment-*` flags can be specified. |
| `--environment-uri-values` | [ENVIRONMENT_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--environment-*` flags can be specified. |
| `--management-url-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Required, The attribute values in case attribute data type is enum. Same `description`/`displayName`/`id`/`immutable` key semantics as `--deployment-type-enum-values`. Shorthand example: `--management-url-enum-values=description=string,displayName=string,id=string,immutable=boolean`; also accepts JSON or `path_to_file.(yaml\|json)`. At most one of the four `--management-url-*` flags can be specified. |
| `--management-url-json-values` | [MANAGEMENT_URL_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--management-url-*` flags can be specified. |
| `--management-url-string-values` | [MANAGEMENT_URL_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--management-url-*` flags can be specified. |
| `--management-url-uri-values` | [MANAGEMENT_URL_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--management-url-*` flags can be specified. |
| `--slo-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Required, The attribute values in case attribute data type is enum. Same `description`/`displayName`/`id`/`immutable` key semantics as `--deployment-type-enum-values`. Shorthand example: `--slo-enum-values=description=string,displayName=string,id=string,immutable=boolean`; also accepts JSON or `path_to_file.(yaml\|json)`. At most one of the four `--slo-*` flags can be specified. |
| `--slo-json-values` | [SLO_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--slo-*` flags can be specified. |
| `--slo-string-values` | [SLO_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--slo-*` flags can be specified. |
| `--slo-uri-values` | [SLO_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--slo-*` flags can be specified. |
| `--source-uri-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Required, The attribute values in case attribute data type is enum. Same `description`/`displayName`/`id`/`immutable` key semantics as `--deployment-type-enum-values`. Shorthand example: `--source-uri-enum-values=description=string,displayName=string,id=string,immutable=boolean`; also accepts JSON or `path_to_file.(yaml\|json)`. At most one of the four `--source-uri-*` flags can be specified. |
| `--source-uri-json-values` | [SOURCE_URI_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--source-uri-*` flags can be specified. |
| `--source-uri-string-values` | [SOURCE_URI_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--source-uri-*` flags can be specified. |
| `--source-uri-values` | [SOURCE_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the four `--source-uri-*` flags can be specified. |

**Examples:**
```bash
To create a deployment with the ID my-deployment, run:

    $ gcloud apihub deployments create --deployment=my-deployment \
        --display-name="My Deployment" --deployment-type=apigee \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/deployments/create)

---
### `gcloud apihub deployments delete`

Delete a Deployment

Delete a deployment.

**Synopsis:**
```
gcloud apihub deployments delete (DEPLOYMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - The name of the deployment resource to delete. Format:
projects/{project}/locations/{location}/deployments/{deployment}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but can
be set in other ways.

To set the project attribute:
 * provide the argument deployment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the deployment.

     To set the deployment attribute:
     + provide the argument deployment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the deployment resource.

     To set the location attribute:
     + provide the argument deployment on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete a deployment with the ID my-deployment, run:

    $ gcloud apihub deployments delete my-deployment \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/deployments/delete)

---
### `gcloud apihub deployments describe`

Describe a Deployment

Describe a deployment.

**Synopsis:**
```
gcloud apihub deployments describe (DEPLOYMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - The name of the deployment resource to retrieve. Format:
projects/{project}/locations/{location}/deployments/{deployment}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but can
be set in other ways.

To set the project attribute:
 * provide the argument deployment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the deployment.

     To set the deployment attribute:
     + provide the argument deployment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the deployment resource.

     To set the location attribute:
     + provide the argument deployment on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a deployment with the ID my-deployment, run:

    $ gcloud apihub deployments describe my-deployment \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/deployments/describe)

---
### `gcloud apihub deployments list`

List Deployments

List deployments.

**Synopsis:**
```
gcloud apihub deployments list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | ID of the location or fully qualified identifier for the location. Location resource - the parent, which owns this collection of deployment resources. Format: `projects/{project}/locations/{location}`. This represents a Cloud resource. To set the project attribute: provide the argument `--location` on the command line with a fully specified name; provide the argument `--project` on the command line; or set the property `core/project`. To set the location attribute: provide the argument `--location` on the command line. This must be specified. |

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
To list all deployments in project my-project and location us-central1, run:

    $ gcloud apihub deployments list --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/deployments/list)

---
### `gcloud apihub deployments update`

Update deployments

Update a deployment.

**Synopsis:**
```
gcloud apihub deployments update (DEPLOYMENT : --location=LOCATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--endpoints=[ENDPOINTS,...]] [--resource-uri=RESOURCE_URI]
    [--source-environment=SOURCE_ENVIRONMENT]
    [--source-project=SOURCE_PROJECT]
    [--attributes=[ATTRIBUTES,...]
      | --update-attributes=[UPDATE_ATTRIBUTES,...] --clear-attributes
      | --remove-attributes=REMOVE_ATTRIBUTES]
    [--clear-deployment-type
      --deployment-type-json-values=[DEPLOYMENT_TYPE_JSON_VALUES,...]
      | --deployment-type-string-values=[DEPLOYMENT_TYPE_STRING_VALUES,...]
      | --deployment-type-uri-values=[DEPLOYMENT_TYPE_URI_VALUES,...]
      | --deployment-type-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-deployment-type-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
        --clear-deployment-type-enum-values
      | --remove-deployment-type-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--clear-documentation
      --documentation-external-uri=DOCUMENTATION_EXTERNAL_URI]
    [--clear-environment
      --environment-json-values=[ENVIRONMENT_JSON_VALUES,...]
      | --environment-string-values=[ENVIRONMENT_STRING_VALUES,...]
      | --environment-uri-values=[ENVIRONMENT_URI_VALUES,...]
      | --environment-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-environment-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
        --clear-environment-enum-values
      | --remove-environment-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--clear-management-url
      --management-url-json-values=[MANAGEMENT_URL_JSON_VALUES,...]
      | --management-url-string-values=[MANAGEMENT_URL_STRING_VALUES,...]
      | --management-url-uri-values=[MANAGEMENT_URL_URI_VALUES,...]
      | --management-url-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-management-url-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
        --clear-management-url-enum-values
      | --remove-management-url-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--clear-slo --slo-json-values=[SLO_JSON_VALUES,...]
      | --slo-string-values=[SLO_STRING_VALUES,...]
      | --slo-uri-values=[SLO_URI_VALUES,...]
      | --slo-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-slo-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
        --clear-slo-enum-values
      | --remove-slo-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [--clear-source-uri
      --source-uri-json-values=[SOURCE_URI_JSON_VALUES,...]
      | --source-uri-string-values=[SOURCE_URI_STRING_VALUES,...]
      | --source-uri-values=[SOURCE_URI_VALUES,...]
      | --source-uri-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
      | --add-source-uri-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]
        --clear-source-uri-enum-values
      | --remove-source-uri-enum-values=[description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - Identifier. The name of the deployment.

Format: projects/{project}/locations/{location}/deployments/{deployment}

The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but can
be set in other ways.

To set the project attribute:
 * provide the argument deployment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the deployment.

     To set the deployment attribute:
     + provide the argument deployment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the deployment resource.

     To set the location attribute:
     + provide the argument deployment on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | The description of the deployment. |
| `--display-name` | DISPLAY_NAME |  | The display name of the deployment. |
| `--endpoints` | [ENDPOINTS,...] |  | The endpoints at which this deployment resource is listening for API requests. This could be a list of complete URIs, hostnames or an IP addresses. |
| `--resource-uri` | RESOURCE_URI |  | The resource URI identifies the deployment within its gateway. For Apigee gateways, its recommended to use the format: organizations/{org}/environments/{env}/apis/{api}. |
| `--source-environment` | SOURCE_ENVIRONMENT |  | The environment at source for the deployment. For example: prod, dev, staging, etc. |
| `--source-project` | SOURCE_PROJECT |  | The project to which the deployment belongs. For Google Cloud gateways, this will refer to the project identifier. For others like Edge/OPDK, this will refer to the org identifier. |
| `--attributes` | [ATTRIBUTES,...] |  | Set attributes to new value. The list of user defined attributes associated with the deployment resource. The key is the attribute name, of the format `projects/{project}/locations/{location}/attributes/{attribute}`; the value is the attribute values associated with the resource. Value sub-fields: `enumValues.values` (enum data type; each value has `description`, `displayName`, `id` — 4-63 characters, valid characters /[a-z][0-9]-/, system generated from display name if not provided; `immutable` — when true, cannot be updated or deleted by the user and can only be true for System defined attributes); `jsonValues.values` (JSON); `stringValues.values` (string); `uriValues.values` (URL, URI or IP, like gs://bucket-name/object-name). Shorthand example: `--attributes=string={enumValues={values=[{description=string,displayName=string,id=string,immutable=boolean}]},jsonValues={values=[string]},stringValues={values=[string]},uriValues={values=[string]}}`; also accepts JSON or `path_to_file.(yaml\|json)`. At most one of `--attributes` or the update/clear/remove attribute flags can be specified. |
| `--update-attributes` | [UPDATE_ATTRIBUTES,...] |  | Update attributes value or add key value pair. The list of user defined attributes associated with the deployment resource (same key format, sub-field structure and shorthand as `--attributes`). Cannot be combined with `--attributes`. |
| `--clear-attributes` |  |  | Clear attributes value and set to empty map. At most one of `--clear-attributes` or `--remove-attributes` can be specified. Cannot be combined with `--attributes`. |
| `--remove-attributes` | REMOVE_ATTRIBUTES |  | Remove existing value from map attributes. Sets remove_attributes value. Shorthand example: `--remove-attributes=string,string`; JSON example: `--remove-attributes=["string"]`; file example: `--remove-attributes=path_to_file.(yaml\|json)`. At most one of `--clear-attributes` or `--remove-attributes` can be specified. Cannot be combined with `--attributes`. |
| `--clear-deployment-type` |  |  | Set googleCloudApihubV1Deployment.deploymentType back to default value. |
| `--deployment-type-json-values` | [DEPLOYMENT_TYPE_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the deployment-type value flags can be specified. |
| `--deployment-type-string-values` | [DEPLOYMENT_TYPE_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the deployment-type value flags can be specified. |
| `--deployment-type-uri-values` | [DEPLOYMENT_TYPE_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the deployment-type value flags can be specified. |
| `--deployment-type-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set deployment_type_enum_values to new value. The attribute values in case attribute data type is enum. Keys: `description` — the detailed description of the allowed value; `displayName` — the display name of the allowed value; `id` — the ID of the allowed value (4-63 characters, valid characters /[a-z][0-9]-/, system generated from display name if not provided; error if already used by another allowed value in the same attribute resource); `immutable` — when true, the allowed value cannot be updated or deleted by the user; only true for System defined attributes. |
| `--add-deployment-type-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to deployment_type_enum_values list. The attribute values in case attribute data type is enum (same keys as `--deployment-type-enum-values`). |
| `--clear-deployment-type-enum-values` |  |  | Clear deployment_type_enum_values value and set to empty list. |
| `--remove-deployment-type-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from deployment_type_enum_values list. The attribute values in case attribute data type is enum (same keys as `--deployment-type-enum-values`). |
| `--clear-documentation` |  |  | Set googleCloudApihubV1Deployment.documentation back to default value. |
| `--documentation-external-uri` | DOCUMENTATION_EXTERNAL_URI |  | The uri of the externally hosted documentation. |
| `--clear-environment` |  |  | Set googleCloudApihubV1Deployment.environment back to default value. |
| `--environment-json-values` | [ENVIRONMENT_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the environment value flags can be specified. |
| `--environment-string-values` | [ENVIRONMENT_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the environment value flags can be specified. |
| `--environment-uri-values` | [ENVIRONMENT_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the environment value flags can be specified. |
| `--environment-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set environment_enum_values to new value. The attribute values in case attribute data type is enum (same keys as `--deployment-type-enum-values`). |
| `--add-environment-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to environment_enum_values list. The attribute values in case attribute data type is enum. |
| `--clear-environment-enum-values` |  |  | Clear environment_enum_values value and set to empty list. |
| `--remove-environment-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from environment_enum_values list. The attribute values in case attribute data type is enum. |
| `--clear-management-url` |  |  | Set googleCloudApihubV1Deployment.managementUrl back to default value. |
| `--management-url-json-values` | [MANAGEMENT_URL_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the management-url value flags can be specified. |
| `--management-url-string-values` | [MANAGEMENT_URL_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the management-url value flags can be specified. |
| `--management-url-uri-values` | [MANAGEMENT_URL_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the management-url value flags can be specified. |
| `--management-url-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set management_url_enum_values to new value. The attribute values in case attribute data type is enum (same keys as `--deployment-type-enum-values`). |
| `--add-management-url-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to management_url_enum_values list. The attribute values in case attribute data type is enum. |
| `--clear-management-url-enum-values` |  |  | Clear management_url_enum_values value and set to empty list. |
| `--remove-management-url-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from management_url_enum_values list. The attribute values in case attribute data type is enum. |
| `--clear-slo` |  |  | Set googleCloudApihubV1Deployment.slo back to default value. |
| `--slo-json-values` | [SLO_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the slo value flags can be specified. |
| `--slo-string-values` | [SLO_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the slo value flags can be specified. |
| `--slo-uri-values` | [SLO_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the slo value flags can be specified. |
| `--slo-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set slo_enum_values to new value. The attribute values in case attribute data type is enum (same keys as `--deployment-type-enum-values`). |
| `--add-slo-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to slo_enum_values list. The attribute values in case attribute data type is enum. |
| `--clear-slo-enum-values` |  |  | Clear slo_enum_values value and set to empty list. |
| `--remove-slo-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from slo_enum_values list. The attribute values in case attribute data type is enum. |
| `--clear-source-uri` |  |  | Set googleCloudApihubV1Deployment.sourceUri back to default value. |
| `--source-uri-json-values` | [SOURCE_URI_JSON_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the source-uri value flags can be specified. |
| `--source-uri-string-values` | [SOURCE_URI_STRING_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the source-uri value flags can be specified. |
| `--source-uri-values` | [SOURCE_URI_VALUES,...] |  | The attribute values in case attribute data type is string or JSON. At most one of the source-uri value flags can be specified. |
| `--source-uri-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Set source_uri_enum_values to new value. The attribute values in case attribute data type is enum (same keys as `--deployment-type-enum-values`). |
| `--add-source-uri-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Add new value to source_uri_enum_values list. The attribute values in case attribute data type is enum. |
| `--clear-source-uri-enum-values` |  |  | Clear source_uri_enum_values value and set to empty list. |
| `--remove-source-uri-enum-values` | [description=DESCRIPTION],[displayName=DISPLAYNAME],[id=ID],[immutable=IMMUTABLE] |  | Remove existing value from source_uri_enum_values list. The attribute values in case attribute data type is enum. |

**Examples:**
```bash
To update a deployment with the ID my-deployment, run:

    $ gcloud apihub deployments update my-deployment \
        --display-name="New Deployment Name" --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/deployments/update)

---
