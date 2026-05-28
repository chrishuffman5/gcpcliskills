# gcloud source-manager repos

manage Secure Source Manager repositories

### `gcloud source-manager repos add-iam-policy-binding`

Add an IAM policy binding to a Secure Source Manager repository

Add an IAM policy binding to a Secure Source Manager repository.

**Synopsis:**
```
gcloud source-manager repos add-iam-policy-binding
    (REPOSITORY : --region=REGION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - Secure Source Manager repository to add the IAM
policy binding to. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument repository on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY
     ID of the repository or fully qualified identifier for the
     repository.

     To set the repository attribute:
     + provide the argument repository on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument repository on the command line with a fully
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
To add an IAM policy binding for the Repository Admin role
(roles/securesourcemanager.repoAdmin) for the user test-user@gmail.com in a
repository named my-repo and location us-central1, run the following
command:

    $ gcloud source-manager repos add-iam-policy-binding my-repo \
        --region=us-central1 --member=user:test-user@gmail.com \
        --role=roles/securesourcemanager.repoAdmin

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/repos/add-iam-policy-binding)

---
### `gcloud source-manager repos create`

Create a Secure Source Manager repository

Create a Secure Source Manager repository.

**Synopsis:**
```
gcloud source-manager repos create (REPOSITORY : --region=REGION)
    --instance=INSTANCE [--description=DESCRIPTION]
    [--default-branch=DEFAULT_BRANCH
      --gitignores=[GITIGNORES,...] --license=LICENSE --readme=README]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - The Secure Source Manager repository to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument repository on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY
     ID of the repository or fully qualified identifier for the
     repository.

     To set the repository attribute:
     + provide the argument repository on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | A Secure Source Manager instance ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the repository. Cannot exceed 500 characters. |


**Examples:**
```bash
To create a repository called 'my-repo' in location 'us-central1' in
instance 'my-instance', run the following command:

    $ gcloud source-manager repos create my-repo --region=us-central1 \
        --instance=my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/repos/create)

---
### `gcloud source-manager repos delete`

Delete a Secure Source Manager repository

Delete a Secure Source Manager repository.

**Synopsis:**
```
gcloud source-manager repos delete (REPOSITORY : --region=REGION)
    [--allow-missing] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - The Secure Source Manager repository to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument repository on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY
     ID of the repository or fully qualified identifier for the
     repository.

     To set the repository attribute:
     + provide the argument repository on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | If set to true, and the resource is not found, the request will succeed but no action will be taken on the server. |


**Examples:**
```bash
To delete a repository called my-repo in location us-central1, run the
following command:

    $ gcloud source-manager repos delete my-repo --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/repos/delete)

---
### `gcloud source-manager repos describe`

Describe a Secure Source Manager repository

Get metadata of a Secure Source Manager repository.

**Synopsis:**
```
gcloud source-manager repos describe (REPOSITORY : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - The Secure Source Manager repository to describe.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument repository on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY
     ID of the repository or fully qualified identifier for the
     repository.

     To set the repository attribute:
     + provide the argument repository on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To describe a repository called my-repo in location us-central1, run the
following command:

    $ gcloud source-manager repos describe my-repo --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/repos/describe)

---
### `gcloud source-manager repos get-iam-policy`

Get the IAM policy for a Secure Source Manager repository

Get the IAM policy for a Secure Source Manager repository.

**Synopsis:**
```
gcloud source-manager repos get-iam-policy (REPOSITORY : --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - Secure Source Manager repository to get the IAM
policy from. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument repository on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY
     ID of the repository or fully qualified identifier for the
     repository.

     To set the repository attribute:
     + provide the argument repository on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To get the IAM policy for an repository named my-repo in location
us-central1, run the following command:

    $ gcloud source-manager repos get-iam-policy my-repo \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/repos/get-iam-policy)

---
### `gcloud source-manager repos list`

List all repositories under a Secure Source Manager instance

List Secure Source Manager repositories.

**Synopsis:**
```
gcloud source-manager repos list --instance=INSTANCE --region=REGION
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | A Secure Source Manager instance ID. |


**Examples:**
```bash
To list repositories in location us-central1 under instance my-instance,
run the following command:

    $ gcloud source-manager repos list --region=us-central1 \
        --instance=my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/repos/list)

---
### `gcloud source-manager repos remove-iam-policy-binding`

Remove an IAM policy binding from a Secure Source Manager repository

Remove an IAM policy binding to a Secure Source Manager repository.

**Synopsis:**
```
gcloud source-manager repos remove-iam-policy-binding
    (REPOSITORY : --region=REGION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - Secure Source Manager repository to remove the IAM
policy binding from. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument repository on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY
     ID of the repository or fully qualified identifier for the
     repository.

     To set the repository attribute:
     + provide the argument repository on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument repository on the command line with a fully
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
To remove the Repository Admin IAM role
(roles/securesourcemanager.repoAdmin) binding from the user
test-user@gmail.com in a repository named my-repo and location us-central1,
run the following command:

    $ gcloud source-manager repos remove-iam-policy-binding my-repo \
        --region=us-central1 --member=user:test-user@gmail.com \
        --role=roles/securesourcemanager.repoAdmin

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/repos/remove-iam-policy-binding)

---
### `gcloud source-manager repos set-iam-policy`

Set the IAM policy for a Secure Source Manager repository

Set the IAM policy for a Secure Source Manager repository.

**Synopsis:**
```
gcloud source-manager repos set-iam-policy (REPOSITORY : --region=REGION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - Secure Source Manager repository to set the IAM
policy on. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument repository on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY
     ID of the repository or fully qualified identifier for the
     repository.

     To set the repository attribute:
     + provide the argument repository on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument repository on the command line with a fully
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
To set the IAM policy for a repository named my-repo in location us-central
to the content of policy.json , run the following command:

    $ gcloud source-manager repos set-iam-policy my-repo \
        --region=us-central1 policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/repos/set-iam-policy)

---
### `gcloud source-manager repos update`

Update a Secure Source Manager repository

Update a Secure Source Manager repository.

**Synopsis:**
```
gcloud source-manager repos update (REPOSITORY : --region=REGION)
    [--description=DESCRIPTION] [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - The Secure Source Manager repository to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument repository on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPOSITORY
     ID of the repository or fully qualified identifier for the
     repository.

     To set the repository attribute:
     + provide the argument repository on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the repository. Cannot exceed 500 characters. |
| `--validate-only` |  |  | If set to true, the request is validated and the user is provided with an expected result, but no actual change is made. |


**Examples:**
```bash
To update the description of a repository called my-repo in location
us-central1, run the following command:

    $ gcloud source-manager repos update my-repo \
        --description="new description" --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/repos/update)

---