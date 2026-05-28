# gcloud service-directory namespaces

manage Service Directory namespaces

### `gcloud service-directory namespaces add-iam-policy-binding`

Adds IAM policy binding to a namespace

Adds IAM policy binding to a namespace.

**Synopsis:**
```
gcloud service-directory namespaces add-iam-policy-binding
    (NAMESPACE : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The Service Directory namespace to add IAM policy
binding to. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument namespace on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

     To set the namespace attribute:
     + provide the argument namespace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the namespace.

     To set the location attribute:
     + provide the argument namespace on the command line with a fully
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
To add an IAM policy binding to a Service Directory namespace, run:

    $ gcloud service-directory namespaces add-iam-policy-binding \
        my-namespace --location=us-east1 --role=roles/owner \
        --member=user:foo@gmail.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/namespaces/add-iam-policy-binding)

---
### `gcloud service-directory namespaces create`

Creates a namespace

Creates a namespace.

**Synopsis:**
```
gcloud service-directory namespaces create
    (NAMESPACE : --location=LOCATION) [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The Service Directory namespace to create. The
namespace id must be 1-63 characters long and match the regular expression
[a-z](?:[-a-z0-9]{0,61}[a-z0-9])? which means the first character must be
a lowercase letter, and all following characters must be a dash, lowercase
letter, or digit, except the last character, which cannot be a dash. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument namespace on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

     To set the namespace attribute:
     + provide the argument namespace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the namespace.

     To set the location attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | Resource labels associated with the namespace. |


**Examples:**
```bash
To create a Service Directory namespace, run:

    $ gcloud service-directory namespaces create my-namespace \
        --location=us-east1 --labels=a=b,c=d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/namespaces/create)

---
### `gcloud service-directory namespaces delete`

Deletes a namespace

Deletes a namespace.

**Synopsis:**
```
gcloud service-directory namespaces delete
    (NAMESPACE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The Service Directory namespace to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument namespace on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

     To set the namespace attribute:
     + provide the argument namespace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the namespace.

     To set the location attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete a Service Directory namespace, run:

    $ gcloud service-directory namespaces delete my-namespace \
        --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/namespaces/delete)

---
### `gcloud service-directory namespaces describe`

Describes a namespace

Describes a namespace.

**Synopsis:**
```
gcloud service-directory namespaces describe
    (NAMESPACE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The Service Directory namespace to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument namespace on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

     To set the namespace attribute:
     + provide the argument namespace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the namespace.

     To set the location attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a Service Directory namespace, run:

    $ gcloud service-directory namespaces describe my-namespace \
        --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/namespaces/describe)

---
### `gcloud service-directory namespaces get-iam-policy`

Gets IAM policy for a namespace

Gets IAM policy for a namespace.

**Synopsis:**
```
gcloud service-directory namespaces get-iam-policy
    (NAMESPACE : --location=LOCATION) [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The Service Directory namespace for which to get IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument namespace on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

     To set the namespace attribute:
     + provide the argument namespace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the namespace.

     To set the location attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get an IAM policy to a Service Directory namespace, run:

    $ gcloud service-directory namespaces get-iam-policy my-namespace \
        --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/namespaces/get-iam-policy)

---
### `gcloud service-directory namespaces list`

Lists namespaces

Lists namespaces.

**Synopsis:**
```
gcloud service-directory namespaces list --location=LOCATION
    [--filter=EXPRESSION] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list Service Directory namespaces, run:

    $ gcloud service-directory namespaces list --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/namespaces/list)

---
### `gcloud service-directory namespaces remove-iam-policy-binding`

Removes IAM policy binding from a namespace

Removes IAM policy binding from a namespace.

**Synopsis:**
```
gcloud service-directory namespaces remove-iam-policy-binding
    (NAMESPACE : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The Service Directory namespace to remove IAM policy
binding from. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument namespace on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

     To set the namespace attribute:
     + provide the argument namespace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the namespace.

     To set the location attribute:
     + provide the argument namespace on the command line with a fully
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
To remove an IAM policy binding to a Service Directory namespace, run:

    $ gcloud service-directory namespaces remove-iam-policy-binding \
        my-namespace --location=us-east1 --role=roles/owner \
        --member=user:foo@gmail.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/namespaces/remove-iam-policy-binding)

---
### `gcloud service-directory namespaces set-iam-policy`

Sets IAM policy for a namespace

Sets IAM policy for a namespace.

**Synopsis:**
```
gcloud service-directory namespaces set-iam-policy
    (NAMESPACE : --location=LOCATION) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The Service Directory namespace to add IAM policy
binding to. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument namespace on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

     To set the namespace attribute:
     + provide the argument namespace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the namespace.

     To set the location attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
To set an IAM policy to a Service Directory namespace, run:

    $ gcloud service-directory namespaces set-iam-policy my-namespace \
        --location=us-east1 policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/namespaces/set-iam-policy)

---
### `gcloud service-directory namespaces update`

Updates a namespace

Updates a namespace.

**Synopsis:**
```
gcloud service-directory namespaces update
    (NAMESPACE : --location=LOCATION) [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The Service Directory namespace to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument namespace on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

     To set the namespace attribute:
     + provide the argument namespace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the namespace.

     To set the location attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | Resource labels associated with the namespace. |


**Examples:**
```bash
To update a Service Directory namespace, run:

    $ gcloud service-directory namespaces update my-namespace \
        --location=us-east1 --labels=a=b,c=d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/namespaces/update)

---