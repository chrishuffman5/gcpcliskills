# gcloud service-directory services

manage Service Directory services

### `gcloud service-directory services add-iam-policy-binding`

Adds IAM policy binding to a service

Adds IAM policy binding to a service.

**Synopsis:**
```
gcloud service-directory services add-iam-policy-binding
    (SERVICE : --location=LOCATION --namespace=NAMESPACE)
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The Service Directory service to add IAM policy binding
to. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the service.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The name of the namespace for the service.

     To set the namespace attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding to a Service Directory service, run:

    $ gcloud service-directory services add-iam-policy-binding \
        my-service --namespace=my-namespace --location=us-east1 \
        --role=roles/owner --member=user:foo@gmail.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/services/add-iam-policy-binding)

---
### `gcloud service-directory services create`

Creates a service

Creates a service.

**Synopsis:**
```
gcloud service-directory services create
    (SERVICE : --location=LOCATION --namespace=NAMESPACE)
    [--annotations=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The Service Directory service to create. The service id
must be 1-63 characters long and match the regular expression
[a-z](?:[-a-z0-9]{0,61}[a-z0-9])? which means the first character must be
a lowercase letter, and all following characters must be a dash, lowercase
letter, or digit, except the last character, which cannot be a dash. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the service.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The name of the namespace for the service.

     To set the namespace attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [KEY=VALUE,...] |  | Annotations for the service. Annotations take the form of key/value string pairs. Keys are composed of an optional prefix and a name segment, separated by a slash(/). Prefixes and names must be composed of alphanumeric characters, dashes, and dots. Names may also use underscores. There are no character restrictions on what may go into the value of an annotation. The entire dictionary is limited to 2000 characters, spread across all key-value pairs. |


**Examples:**
```bash
To create a Service Directory service, run:

    $ gcloud service-directory services create my-service \
        --namespace=my-namespace --location=us-east1 \
        --annotations=a=b,c=d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/services/create)

---
### `gcloud service-directory services delete`

Deletes a service

Deletes a service.

**Synopsis:**
```
gcloud service-directory services delete
    (SERVICE : --location=LOCATION --namespace=NAMESPACE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The Service Directory service to delete. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the service.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The name of the namespace for the service.

     To set the namespace attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.
```

**Examples:**
```bash
To delete a Service Directory service, run:

    $ gcloud service-directory services delete my-service \
        --namespace=my-namespace --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/services/delete)

---
### `gcloud service-directory services describe`

Describes a service

Describes a service.

**Synopsis:**
```
gcloud service-directory services describe
    (SERVICE : --location=LOCATION --namespace=NAMESPACE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The Service Directory service to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the service.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The name of the namespace for the service.

     To set the namespace attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.
```

**Examples:**
```bash
To describe a Service Directory service, run:

    $ gcloud service-directory services describe my-service \
        --namespace=my-namespace --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/services/describe)

---
### `gcloud service-directory services get-iam-policy`

Gets IAM policy for a service

Gets IAM policy for a service.

**Synopsis:**
```
gcloud service-directory services get-iam-policy
    (SERVICE : --location=LOCATION --namespace=NAMESPACE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The Service Directory service for which to get IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the service.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The name of the namespace for the service.

     To set the namespace attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.
```

**Examples:**
```bash
To get an IAM policy to a Service Directory service, run:

    $ gcloud service-directory services get-iam-policy my-service \
        --namespace=my-namespace --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/services/get-iam-policy)

---
### `gcloud service-directory services list`

Lists services

Lists services.

**Synopsis:**
```
gcloud service-directory services list
    (--namespace=NAMESPACE : --location=LOCATION) [--filter=EXPRESSION]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--namespace` | NAMESPACE |  | _[This must be specified.]_ ID of the namespace or fully qualified identifier for the namespace. To set the namespace attribute: + provide the argument --namespace on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The name of the region for the namespace. To set the location attribute: + provide the argument --namespace on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list Service Directory services, run:

    $ gcloud service-directory services list --namespace=my-namespace \
        --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/services/list)

---
### `gcloud service-directory services remove-iam-policy-binding`

Removes IAM policy binding from a service

Removes IAM policy binding from a service.

**Synopsis:**
```
gcloud service-directory services remove-iam-policy-binding
    (SERVICE : --location=LOCATION --namespace=NAMESPACE)
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The Service Directory service to remove IAM policy
binding from. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the service.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The name of the namespace for the service.

     To set the namespace attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding to a Service Directory service, run:

    $ gcloud service-directory services remove-iam-policy-binding \
        my-service --namespace=my-namespace --location=us-east1 \
        --role=roles/owner --member=user:foo@gmail.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/services/remove-iam-policy-binding)

---
### `gcloud service-directory services resolve`

Resolves a service

Resolves a service.

**Synopsis:**
```
gcloud service-directory services resolve
    (SERVICE : --location=LOCATION --namespace=NAMESPACE)
    [--endpoint-filter=ENDPOINT_FILTER] [--max-endpoints=MAX_ENDPOINTS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The Service Directory service to resolve. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the service.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The name of the namespace for the service.

     To set the namespace attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--endpoint-filter` | ENDPOINT_FILTER |  | Apply a Boolean filter EXPRESSION to each endpoint in the service. If the expression evaluates True, then that endpoint is listed. |
| `--max-endpoints` | MAX_ENDPOINTS |  | Maximum number of endpoints to return. |


**Examples:**
```bash
To resolve Service Directory services, run:

    $ gcloud service-directory services resolve my-service \
        --namespace=my-namespace --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/services/resolve)

---
### `gcloud service-directory services set-iam-policy`

Sets IAM policy for a service

Sets IAM policy for a service.

**Synopsis:**
```
gcloud service-directory services set-iam-policy
    (SERVICE : --location=LOCATION --namespace=NAMESPACE) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The Service Directory service to add IAM policy binding
to. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the service.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The name of the namespace for the service.

     To set the namespace attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
To set an IAM policy to a Service Directory service, run:

    $ gcloud service-directory services set-iam-policy my-service \
        --namespace=my-namespace --location=us-east1 policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/services/set-iam-policy)

---
### `gcloud service-directory services update`

Updates a service

Updates a service.

**Synopsis:**
```
gcloud service-directory services update
    (SERVICE : --location=LOCATION --namespace=NAMESPACE)
    [--annotations=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The Service Directory service to update. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the service.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The name of the namespace for the service.

     To set the namespace attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [KEY=VALUE,...] |  | Annotations for the service. Annotations take the form of key/value string pairs. Keys are composed of an optional prefix and a name segment, separated by a slash(/). Prefixes and names must be composed of alphanumeric characters, dashes, and dots. Names may also use underscores. There are no character restrictions on what may go into the value of an annotation. The entire dictionary is limited to 2000 characters, spread across all key-value pairs. |


**Examples:**
```bash
To update a Service Directory service, run:

    $ gcloud service-directory services update my-service \
        --namespace=my-namespace --location=us-east1 \
        --annotations=a=b,c=d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/services/update)

---