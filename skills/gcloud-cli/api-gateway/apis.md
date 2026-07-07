# gcloud api-gateway apis

manage Cloud API Gateway APIs

### `gcloud api-gateway apis add-iam-policy-binding`

Add IAM policy binding to a gateway

Add IAM policy binding to a gateway.

**Synopsis:**
```
gcloud api-gateway apis add-iam-policy-binding API --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Api resource - Name for API which IAM policy binding will be added to.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * Location for API and API Configs. Defaults to global.

This must be specified.

  API
     ID of the api or fully qualified identifier for the api.

     To set the api attribute:
     + provide the argument api on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on the API 'my-api', run:

    $ gcloud api-gateway apis add-iam-policy-binding my-api \
        --member='user:test-user@gmail.com' --role='roles/editor
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/apis/add-iam-policy-binding)

---
### `gcloud api-gateway apis create`

Create a new API

Create a new API.

**Synopsis:**
```
gcloud api-gateway apis create API [--async] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--managed-service=MANAGED_SERVICE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Api resource - Name for API which created. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * Location for API and API Configs. Defaults to global.

This must be specified.

  API
     ID of the api or fully qualified identifier for the api.

     To set the api attribute:
     + provide the argument api on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | Human readable name which can optionally be supplied. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--managed-service` | MANAGED_SERVICE |  | The name of a pre-existing Google Managed Service. |


**Examples:**
```bash
To create an API, run:

    $ gcloud api-gateway apis create my-api
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/apis/create)

---
### `gcloud api-gateway apis delete`

Deletes an API

Deletes an API.

NOTE: All API configs belonging to the API will need to be deleted before
the API can be deleted.

**Synopsis:**
```
gcloud api-gateway apis delete API [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Api resource - Name for API which will be deleted. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * Location for API and API Configs. Defaults to global.

This must be specified.

  API
     ID of the api or fully qualified identifier for the api.

     To set the api attribute:
     + provide the argument api on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an API 'my-api', run:

    $ gcloud api-gateway apis delete my-api

NOTE: All API configs belonging to the API will need to be deleted before
the API can be deleted.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/apis/delete)

---
### `gcloud api-gateway apis describe`

Show details about a specific API

Show details about a specific API.

**Synopsis:**
```
gcloud api-gateway apis describe API [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Api resource - Name for API which will be described. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * Location for API and API Configs. Defaults to global.

This must be specified.

  API
     ID of the api or fully qualified identifier for the api.

     To set the api attribute:
     + provide the argument api on the command line.
```

**Examples:**
```bash
To show details about an API, run:

    $ gcloud api-gateway apis describe my-api
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/apis/describe)

---
### `gcloud api-gateway apis get-iam-policy`

Get the IAM policy for an API

Get the IAM policy for an API.

**Synopsis:**
```
gcloud api-gateway apis get-iam-policy API [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Api resource - Name for API which for which to get IAM policy. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * Location for API and API Configs. Defaults to global.

This must be specified.

  API
     ID of the api or fully qualified identifier for the api.

     To set the api attribute:
     + provide the argument api on the command line.
```

**Examples:**
```bash
To print the IAM policy for a given API, run:

    $ gcloud api-gateway apis get-iam-policy my-api
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/apis/get-iam-policy)

---
### `gcloud api-gateway apis list`

List APIs

List APIs.

**Synopsis:**
```
gcloud api-gateway apis list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all apis, run:

    $ gcloud api-gateway apis list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/apis/list)

---
### `gcloud api-gateway apis remove-iam-policy-binding`

Remove IAM policy binding to a gateway

Remove IAM policy binding to a gateway.

**Synopsis:**
```
gcloud api-gateway apis remove-iam-policy-binding API --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Api resource - Name for API which IAM policy binding will be added to.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * Location for API and API Configs. Defaults to global.

This must be specified.

  API
     ID of the api or fully qualified identifier for the api.

     To set the api attribute:
     + provide the argument api on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on API 'my-api', run:

    $ gcloud api-gateway apis remove-iam-policy-binding my-api \
        --member='user:test-user@gmail.com' --role='roles/editor'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/apis/remove-iam-policy-binding)

---
### `gcloud api-gateway apis update`

Update an API Gateway API

Update an API Gateway API.

NOTE: Only the display name and labels attributes are mutable on an API.

**Synopsis:**
```
gcloud api-gateway apis update API [--async] [--display-name=DISPLAY_NAME]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Api resource - Name for API which updated. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument api on the command line with a fully specified
   name;
 * Location for API and API Configs. Defaults to global.

This must be specified.

  API
     ID of the api or fully qualified identifier for the api.

     To set the api attribute:
     + provide the argument api on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | Human readable name which can optionally be supplied. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the display name of an API, run:

    $ gcloud api-gateway apis update my-api \
        --display-name="New Display Name"

NOTE: Only the display name and labels attributes are mutable on an API.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/apis/update)

---