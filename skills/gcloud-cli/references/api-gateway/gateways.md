# gcloud api-gateway gateways

manage Cloud API Gateway Gateways

### `gcloud api-gateway gateways add-iam-policy-binding`

Add IAM policy binding to a gateway

Add IAM policy binding to a gateway.

**Synopsis:**
```
gcloud api-gateway gateways add-iam-policy-binding
    (GATEWAY : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Gateway resource - Name for gateway which will be IAM policy binding will
be added to. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument gateway on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GATEWAY
     ID of the gateway or fully qualified identifier for the gateway.

     To set the gateway attribute:
     + provide the argument gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud location for gateway.

     To set the location attribute:
     + provide the argument gateway on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on the gateway 'my-gateway', run:

    $ gcloud api-gateway gateways add-iam-policy-binding my-gateway \
        --member='user:test-user@gmail.com' --role='roles/editor
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/gateways/add-iam-policy-binding)

---
### `gcloud api-gateway gateways create`

Create a new gateway

Create a new gateway.

**Synopsis:**
```
gcloud api-gateway gateways create (GATEWAY : --location=LOCATION)
    (--api-config=API_CONFIG : --api=API) [--async]
    [--display-name=DISPLAY_NAME] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Gateway resource - Name for gateway which will be created. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument gateway on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GATEWAY
     ID of the gateway or fully qualified identifier for the gateway.

     To set the gateway attribute:
     + provide the argument gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud location for gateway.

     To set the location attribute:
     + provide the argument gateway on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--api-config` | API_CONFIG |  | _[This must be specified.]_ ID of the api-config or fully qualified identifier for the api-config. To set the api-config attribute: + provide the argument --api-config on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--api` | API |  | _[This must be specified.]_ API ID. To set the api attribute: + provide the argument --api-config on the command line with a fully specified name; + provide the argument --api on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | Human readable name which can optionally be supplied. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a gateway in 'us-central1' run:

    $ gcloud api-gateway gateways create my-gateway --api=my-api \
        --api-config=my-config --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/gateways/create)

---
### `gcloud api-gateway gateways delete`

Delete an API Gateway

Delete an API Gateway.

**Synopsis:**
```
gcloud api-gateway gateways delete (GATEWAY : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Gateway resource - Name for gateway which will be deleted. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument gateway on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GATEWAY
     ID of the gateway or fully qualified identifier for the gateway.

     To set the gateway attribute:
     + provide the argument gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud location for gateway.

     To set the location attribute:
     + provide the argument gateway on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a gateway 'my-gateway' in 'us-central1', run:

    $ gcloud api-gateway gateways delete my-gateway \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/gateways/delete)

---
### `gcloud api-gateway gateways describe`

Show details about a specific gateway

Show details about a specific gateway.

**Synopsis:**
```
gcloud api-gateway gateways describe (GATEWAY : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Gateway resource - Name for gateway which will be created. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument gateway on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GATEWAY
     ID of the gateway or fully qualified identifier for the gateway.

     To set the gateway attribute:
     + provide the argument gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud location for gateway.

     To set the location attribute:
     + provide the argument gateway on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To show details about a Gateway in us-central1, run:

    $ gcloud api-gateway gateways describe my-gateway \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/gateways/describe)

---
### `gcloud api-gateway gateways get-iam-policy`

Get the IAM policy for a gateway

Get the IAM policy for a gateway.

**Synopsis:**
```
gcloud api-gateway gateways get-iam-policy (GATEWAY : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Gateway resource - Name for gateway which will be for which to get IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument gateway on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GATEWAY
     ID of the gateway or fully qualified identifier for the gateway.

     To set the gateway attribute:
     + provide the argument gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud location for gateway.

     To set the location attribute:
     + provide the argument gateway on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To print the IAM policy for a given gateway, run:

    $ gcloud api-gateway gateways get-iam-policy my-gateway \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/gateways/get-iam-policy)

---
### `gcloud api-gateway gateways list`

List API Gateways

List API Gateways.

**Synopsis:**
```
gcloud api-gateway gateways list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + Location for API and API Configs. Defaults to a wildcard. |


**Examples:**
```bash
To list all gateways, run:

    $ gcloud api-gateway gateways list

To list all gateways within the 'us-central1' location:

    $ gcloud api-gateway gateways list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/gateways/list)

---
### `gcloud api-gateway gateways remove-iam-policy-binding`

Remove IAM policy binding from a gateway

Remove IAM policy binding from a gateway.

**Synopsis:**
```
gcloud api-gateway gateways remove-iam-policy-binding
    (GATEWAY : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Gateway resource - Name for gateway which will be IAM policy binding will
be added to. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument gateway on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GATEWAY
     ID of the gateway or fully qualified identifier for the gateway.

     To set the gateway attribute:
     + provide the argument gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud location for gateway.

     To set the location attribute:
     + provide the argument gateway on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on Gateway 'my-gateway' in us-central1, run:

    $ gcloud api-gateway gateways remove-iam-policy-binding my-gateway \
        --location='us-central1' --member='user:test-user@gmail.com' \
        --role='roles/editor'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/gateways/remove-iam-policy-binding)

---
### `gcloud api-gateway gateways update`

Update an API Gateway

Update an API Gateway.

**Synopsis:**
```
gcloud api-gateway gateways update (GATEWAY : --location=LOCATION)
    [--async] [--display-name=DISPLAY_NAME]
    [--update-labels=[KEY=VALUE,...]] [--api-config=API_CONFIG : --api=API]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Gateway resource - Name for gateway which will be updated. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument gateway on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GATEWAY
     ID of the gateway or fully qualified identifier for the gateway.

     To set the gateway attribute:
     + provide the argument gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud location for gateway.

     To set the location attribute:
     + provide the argument gateway on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | Human readable name which can optionally be supplied. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the display name of a gateway, run:

    $ gcloud api-gateway gateways update my-gateway \
        --location=us-central1 --display-name="New Display Name"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/gateways/update)

---