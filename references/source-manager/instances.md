# gcloud source-manager instances

manage Secure Source Manager instances

### `gcloud source-manager instances add-iam-policy-binding`

Add an IAM policy binding to a Secure Source Manager instance

Add an IAM policy binding to a Secure Source Manager instance.

**Synopsis:**
```
gcloud source-manager instances add-iam-policy-binding
    (INSTANCE : --region=REGION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance for which to add the IAM policy binding.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' with instance named 'my-instance' and location
'us-central1', run:

    $ gcloud source-manager instances add-iam-policy-binding \
        my-instance --region='us-central1' \
        --member='user:test-user@gmail.com' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/instances/add-iam-policy-binding)

---
### `gcloud source-manager instances create`

Create a Secure Source Manager instance

Create a Secure Source Manager instance.

**Synopsis:**
```
gcloud source-manager instances create (INSTANCE : --region=REGION)
    [--async] [--enable-workforce-identity-federation] [--kms-key=KMS_KEY]
    [--max-wait=MAX_WAIT; default="60m"]
    [--is-private
      : --ca-pool=CA_POOL --psc-allowed-projects=[PROJECTS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The Secure Source Manager instance to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--enable-workforce-identity-federation` |  |  | Bool indicator for workforce identity federation instance. |
| `--kms-key` | KMS_KEY |  | KMS key used to encrypt instance optionally. |
| `--max-wait` | MAX_WAIT | 60m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To create a Secure Source Manager instance named 'my-instance' in location
'us-central1' asynchronously, run:

    $ gcloud source-manager instances create my-instance \
        --region=us-central1

To create a Secure Source Manager instance named 'my-instance' in location
'us-central1' synchronously, and wait a maximum of 30 minutes for it to
finish being created, run:

    $ gcloud source-manager instances create my-instance \
        --region=us-central1 --no-async --max-wait=30m
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/instances/create)

---
### `gcloud source-manager instances delete`

Delete a Secure Source Manager instance

Delete a Secure Source Manager instance.

**Synopsis:**
```
gcloud source-manager instances delete (INSTANCE : --region=REGION)
    [--async] [--max-wait=MAX_WAIT; default="60m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The Secure Source Manager instance to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--max-wait` | MAX_WAIT | 60m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To delete a Secure Source Manager instance named 'my-instance' in location
'us-central1' asynchronously, run:

    $ gcloud source-manager instances delete my-instance \
        --region=us-central1

To delete a Secure Source Manager instance named 'my-instance' in location
'us-central1' synchronously, and wait a maximum of 30 minutes for it to
finish being deleted, run:

    $ gcloud source-manager instances delete my-instance \
        --region=us-central1 --no-async --max-wait=30m
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/instances/delete)

---
### `gcloud source-manager instances describe`

Describe a Secure Source Manager instance

Get details of a Secure Source Manager instance.

**Synopsis:**
```
gcloud source-manager instances describe (INSTANCE : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance you want to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To describe a Secure Source Manager instance named 'my-instance' in
location 'us-central1' under the current project, run:

    $ gcloud source-manager instances describe my-instance \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/instances/describe)

---
### `gcloud source-manager instances get-iam-policy`

Get the IAM policy for a Secure Source Manager instance

Get the IAM policy for a Secure Source Manager instance.

**Synopsis:**
```
gcloud source-manager instances get-iam-policy (INSTANCE : --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The Secure Source Manager instance for which to get
the IAM policy. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To get the IAM policy for an instance named 'my-instance' in location
'us-central1', run:

    $ gcloud source-manager instances get-iam-policy my-instance \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/instances/get-iam-policy)

---
### `gcloud source-manager instances list`

List Secure Source Manager instances

List all instances on your Secure Source Manager.

**Synopsis:**
```
gcloud source-manager instances list --region=REGION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list all Secure Source Manager instances in location 'us-central1' under
the current project, run:

    $ gcloud source-manager instances list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/instances/list)

---
### `gcloud source-manager instances remove-iam-policy-binding`

Remove an IAM policy binding to a Secure Source Manager instance

Remove an IAM policy binding to a Secure Source Manager instance.

**Synopsis:**
```
gcloud source-manager instances remove-iam-policy-binding
    (INSTANCE : --region=REGION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance for which to remove the IAM policy
binding. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' with instance named 'my-instance' and location
'us-central1', run:

    $ gcloud source-manager instances remove-iam-policy-binding \
        my-instance --region='us-central1' \
        --member='user:test-user@gmail.com' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/instances/remove-iam-policy-binding)

---
### `gcloud source-manager instances set-iam-policy`

Set the IAM policy for a Secure Source Manager instance

Set the IAM policy for a Secure Source Manager instance.

**Synopsis:**
```
gcloud source-manager instances set-iam-policy (INSTANCE : --region=REGION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The Secure Source Manager instance for which to set
the IAM policy. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
To set the IAM policy for an instance named 'my-instance' in location
'us-central' to content of policy.json , run:

    $ gcloud source-manager instances set-iam-policy my-instance \
        --region=us-central1 policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/instances/set-iam-policy)

---