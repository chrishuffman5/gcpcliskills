# gcloud endpoints services

manage Services

### `gcloud endpoints services add-iam-policy-binding`

Add IAM policy binding to a service

Add an IAM policy binding to a service.

Note: The 'roles/servicemanagement.serviceConsumer' role can only be added
to a member which is a user, group, or service account.

**Synopsis:**
```
gcloud endpoints services add-iam-policy-binding SERVICE --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The service for which to add IAM policy binding to.
This represents a Cloud resource.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding with the role of
'roles/servicemanagement.serviceConsumer' for the user
'test-user@example.com' on the service 'my-service', run:

    $ gcloud endpoints services add-iam-policy-binding my-service \
        --member='user:test-user@example.com' \
        --role='roles/servicemanagement.serviceConsumer'

To add an IAM policy binding with the role of
'roles/servicemanagement.serviceConsumer' for the service account
'my-iam-account@my-project.iam.gserviceaccount.com' on the service
'my-service', run:

    $ gcloud endpoints services add-iam-policy-binding my-service \
        --member='serviceAccount:my-iam-account@my-project.iam.gservicea\
    ccount.com' --role='roles/servicemanagement.serviceConsumer'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/endpoints/services/add-iam-policy-binding)

---
### `gcloud endpoints services check-iam-policy`

Returns information about a principal's permissions on a service

This command lists the permissions that the current authenticated gcloud
user has for a service. For example, if the authenticated user is able to
delete the service, servicemanagement.services.delete will be among the
returned permissions.

**Synopsis:**
```
gcloud endpoints services check-iam-policy SERVICE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE
   The name of the service for which to check the IAM policy.
```

**Examples:**
```bash
To check the permissions for the currently authenticated gcloud, run:

    $ gcloud endpoints services check-iam-policy my_produced_service_name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/endpoints/services/check-iam-policy)

---
### `gcloud endpoints services delete`

Deletes a service from Google Service Management

Services that are deleted will be retained in the system for 30 days. If a
deleted service is still within this retention window, it can be undeleted
with the undelete command.

**Synopsis:**
```
gcloud endpoints services delete SERVICE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE
   The name of the service to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a service named my-service, run:

    $ gcloud endpoints services delete my-service

To run the same command asynchronously (non-blocking), run:

    $ gcloud endpoints services delete my-service --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/endpoints/services/delete)

---
### `gcloud endpoints services deploy`

Deploys a service configuration for the given service name

This command is used to deploy a service configuration for a service to
Google Service Management. As input, it takes one or more paths to service
configurations that should be uploaded. These configuration files can be
Proto Descriptors, Open API (Swagger) specifications, or Google Service
Configuration files in JSON or YAML formats.

If a service name is present in multiple configuration files (given in the
host field in OpenAPI specifications or the name field in Google Service
Configuration files), the first one will take precedence.

This command will block until deployment is complete unless the --async
flag is passed.

**Synopsis:**
```
gcloud endpoints services deploy SERVICE_CONFIG_FILE
    [SERVICE_CONFIG_FILE ...] [--async] [--force, -f] [--validate-only]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE_CONFIG_FILE [SERVICE_CONFIG_FILE ...]
   The service configuration file (or files) containing the API
   specification to upload. Proto Descriptors, Open API (Swagger)
   specifications, and Google Service Configuration files in JSON and YAML
   formats are acceptable.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force, -f` |  |  | Force the deployment even if any hazardous changes to the service configuration are detected. |
| `--validate-only` |  |  | If included, the command validates the service configuration(s), but does not deploy them. The service must exist in order to validate the configuration(s). |


**Examples:**
```bash
To deploy a single Open API service configuration, run:

    $ gcloud endpoints services deploy ~/my_app/openapi.json

To run the deployment asynchronously (non-blocking), run:

    $ gcloud endpoints services deploy ~/my_app/openapi.json --async

To deploy a service config with a Proto, run:

    $ gcloud endpoints services deploy ~/my_app/service-config.yaml \
        ~/my_app/service-protos.pb
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/endpoints/services/deploy)

---
### `gcloud endpoints services describe`

Describes a service given a service name

Describes a service given a service name.

**Synopsis:**
```
gcloud endpoints services describe SERVICE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE
   The name of the service to describe.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/endpoints/services/describe)

---
### `gcloud endpoints services get-iam-policy`

Describes the IAM policy for a service

Gets the IAM policy for a produced service, given the service name.

**Synopsis:**
```
gcloud endpoints services get-iam-policy SERVICE [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE
   The name of the service whose IAM policy is to be described.
```

**Examples:**
```bash
To print the IAM policy for a service named my-service, run:

    $ gcloud endpoints services get-iam-policy my-service
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/endpoints/services/get-iam-policy)

---
### `gcloud endpoints services list`

List services for a project

This command lists the services that are produced by a project.

**Synopsis:**
```
gcloud endpoints services list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list the services the current project produces, run:

    $ gcloud endpoints services list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/endpoints/services/list)

---
### `gcloud endpoints services remove-iam-policy-binding`

Remove IAM policy binding from a service

Remove an IAM policy binding from a service.

Note: The 'roles/servicemanagement.serviceConsumer' role can only exist on
a member which is a user, group, or service account.

**Synopsis:**
```
gcloud endpoints services remove-iam-policy-binding SERVICE
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The device registry for which to remove IAM policy
binding from. This represents a Cloud resource.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of
'roles/servicemanagement.serviceConsumer' for the user
'test-user@gmail.com' with service 'my-service', run:

    $ gcloud endpoints services remove-iam-policy-binding my-service \
        --member='user:test-user@gmail.com' \
        --role='roles/servicemanagement.serviceConsumer'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/endpoints/services/remove-iam-policy-binding)

---
### `gcloud endpoints services undelete`

Undeletes a service configuration that was previously deleted

Services that are deleted will be retained in the system for 30 days. If a
deleted service is still within this retention window, it can be undeleted
with this command.

Note that this means that this command will not be effective for service
configurations marked for deletion more than 30 days ago.

**Synopsis:**
```
gcloud endpoints services undelete SERVICE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE
   The name of the service to undelete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To undelete a service named my-service, run:

    $ gcloud endpoints services undelete my-service

To run the same command asynchronously (non-blocking), run:

    $ gcloud endpoints services undelete my-service --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/endpoints/services/undelete)

---