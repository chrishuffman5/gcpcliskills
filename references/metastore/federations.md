# gcloud metastore federations

manage Dataproc Metastore federations

### `gcloud metastore federations add-iam-policy-binding`

Add an IAM policy binding to a federation

Add an IAM policy binding to a federation.

**Synopsis:**
```
gcloud metastore federations add-iam-policy-binding
    (FEDERATION : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Federation resource - Federation for which to add the IAM policy to. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument federation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FEDERATION
     ID of the federation or fully qualified identifier for the
     federation.

     To set the federation attribute:
     + provide the argument federation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument federation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of roles/metastore.admin for the
user test-user@gmail.com, run:

    $ gcloud metastore federations add-iam-policy-binding \
        my-federation --member='user:test-user@gmail.com' \
        --role='roles/metastore.admin'

See https://cloud.google.com/dataproc-metastore/docs/iam-and-access-control
for details of policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/federations/add-iam-policy-binding)

---
### `gcloud metastore federations create`

Create a Dataproc Metastore federation

Create a new Dataproc Metastore federation with the given name and
configurations.

If run asynchronously with --async, exits after printing one operation name
that can be used to poll the status of the creation via:

    gcloud metastore operations describe

**Synopsis:**
```
gcloud metastore federations create (FEDERATION : --location=LOCATION)
    --backends=RANK=BACKEND [--async]
    [--hive-metastore-version=HIVE_METASTORE_VERSION]
    [--labels=[KEY=VALUE,...]] [--tags=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Federation resource - Arguments and flags that specify the Dataproc
Metastore federation you want to create. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument federation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FEDERATION
     ID of the federation or fully qualified identifier for the
     federation.

     To set the federation attribute:
     + provide the argument federation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument federation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backends` | RANK=BACKEND |  | Backends from which the federation service serves metadata at query time. The backends are specified as a comma-separated list of RANK=BACKEND pairs. For example: 1=dpms:dpms1,2=dpms:projects/my-project/locations/us-central1/services/dpms2. RANK represents the rank of the backend metastore and is used to resolve database name collisions. BACKEND is specified as METASTORE_TYPE:METASTORE_NAME where METASTORE_TYPE is the type of backend metastore and METASTORE_NAME is the relative resource name of the metastore. If only the name of the metastore is specified (e.g. dpms1), project and location will be inferred from the project and location used to create the federation. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--hive-metastore-version` | one of: 2.3.6, 3.1.2 |  | Hive metastore schema version of the Metastore federation. HIVE_METASTORE_VERSION must be one of: 2.3.6, 3.1.2. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--tags` | [KEY=VALUE,...] |  | List of tag KEY=VALUE pairs to add. |


**Examples:**
```bash
To create a Dataproc Metastore federation with the name
my-metastore-federation in location us-central with two backends dpms1 and
dpms2, run:

    $ gcloud metastore federations create my-metastore-federation \
      --location=us-central1 \
      --backends=1=dpms:dpms1,2=dpms:projects/my-project/locations/\
    us-central1/services/dpms2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/federations/create)

---
### `gcloud metastore federations delete`

Delete one or more Dataproc Metastore federations

If run asynchronously with --async, exits after printing one or more
operation names that can be used to poll the status of the deletion(s) via:

    gcloud metastore operations describe

**Synopsis:**
```
gcloud metastore federations delete
    (FEDERATIONS [FEDERATIONS ...] : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Federation resource - The federations to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument federations on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FEDERATIONS [FEDERATIONS ...]
     IDs of the federations or fully qualified identifiers for the
     federations.

     To set the federation attribute:
     + provide the argument federations on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location to which the federations belongs.

     To set the location attribute:
     + provide the argument federations on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a Dataproc Metastore federation with the name
my-metastore-federation in location us-central1, run:

    $ gcloud metastore federations delete my-metastore-federation \
        --location=us-central1

To delete multiple Dataproc Metastore federations with the name
federation-1 and federation-2 in the same location us-central1, run:

    $ gcloud metastore federations delete federation-1 federation-2 \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/federations/delete)

---
### `gcloud metastore federations describe`

Describe a Dataproc Metastore federation

Describe a Dataproc Metastore federation.

Displays all details of a Dataproc Metastore federation given a valid
federation ID.

**Synopsis:**
```
gcloud metastore federations describe (FEDERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Federation resource - Arguments and flags that specify the Metastore
federation you want to describe. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument federation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FEDERATION
     ID of the federation or fully qualified identifier for the
     federation.

     To set the federation attribute:
     + provide the argument federation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument federation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Examples:**
```bash
To describe a Dataproc Metastore federation with the ID
my-metastore-federation in us-central1, run:

    $ gcloud metastore federations describe my-metastore-federation \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/federations/describe)

---
### `gcloud metastore federations get-iam-policy`

Get the IAM policy for the federation

gcloud metastore federations get-iam-policy displays the IAM policy
associated with the federation. If formatted as JSON, the output can be
edited and used as a policy file for set-iam-policy. The output includes an
"etag" field identifying the version emitted and allowing detection of
concurrent policy updates. The "etag" field should be removed to be used as
set-iam-policy input; see gcloud metastore federations set-iam-policy for
additional details.

**Synopsis:**
```
gcloud metastore federations get-iam-policy
    (FEDERATION : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Federation resource - Federation for which to display the IAM policy. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument federation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FEDERATION
     ID of the federation or fully qualified identifier for the
     federation.

     To set the federation attribute:
     + provide the argument federation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument federation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Examples:**
```bash
To print the IAM policy for a given federation, run:

    $ gcloud metastore federations get-iam-policy my-federation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/federations/get-iam-policy)

---
### `gcloud metastore federations list`

List Dataproc Metastore federations

Lists all federations under the specified project and location.

**Synopsis:**
```
gcloud metastore federations list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property metastore/location. |


**Examples:**
```bash
To list all Dataproc Metastore federations in location us-central1, run:

    $ gcloud metastore federations list --location=us-central1

To list all Dataproc Metastore federations in all locations, run:

    $ gcloud metastore federations list --location=-
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/federations/list)

---
### `gcloud metastore federations remove-iam-policy-binding`

Remove an IAM policy binding from a federation

Remove an IAM policy binding from a federation.

**Synopsis:**
```
gcloud metastore federations remove-iam-policy-binding
    (FEDERATION : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Federation resource - Federation for which to remove the IAM policy from.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument federation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FEDERATION
     ID of the federation or fully qualified identifier for the
     federation.

     To set the federation attribute:
     + provide the argument federation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument federation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of roles/metastore.admin for
the user test-user@gmail.com, run:

    $ gcloud metastore federations remove-iam-policy-binding \
        my-federation --member='user:test-user@gmail.com' \
        --role='roles/metastore.admin'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/federations/remove-iam-policy-binding)

---
### `gcloud metastore federations set-iam-policy`

Set the IAM policy for the federation

Sets the IAM policy for the given federation as defined in a JSON or YAML
file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud metastore federations set-iam-policy
    (FEDERATION : --location=LOCATION) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Federation resource - Federation for which to display the IAM policy. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument federation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FEDERATION
     ID of the federation or fully qualified identifier for the
     federation.

     To set the federation attribute:
     + provide the argument federation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument federation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
policy.json and set it for the federation my-federation:

    $ gcloud metastore federations set-iam-policy my-federation \
        policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/federations/set-iam-policy)

---
### `gcloud metastore federations update`

Update a Dataproc Metastore federation

Update the metadata and/or configuration parameters of a Dataproc Metastore
federation.

If run asynchronously with --async, exits after printing one operation name
that can be used to poll the status of the update via:

    gcloud metastore operations describe

**Synopsis:**
```
gcloud metastore federations update (FEDERATION : --location=LOCATION)
    (--update-backends=RANK=BACKEND --clear-backends
      | --remove-backends=RANK) [--async] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Federation resource - Arguments and flags that specify the Dataproc
Metastore federation you want to update. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument federation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FEDERATION
     ID of the federation or fully qualified identifier for the
     federation.

     To set the federation attribute:
     + provide the argument federation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument federation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-backends` | RANK=BACKEND |  | _[At least one of these must be specified:]_ Comma-separated list of metastore backends specified as a list of RANK=BACKEND pairs. For example: 1=dpms:dpms1,2=dpms:projects/my-project/locations/us-central1/services/dpms2. RANK represents the rank of the backend metastore and is used to resolve database name collisions. BACKEND is specified as METASTORE_TYPE:METASTORE_NAME where METASTORE_TYPE is the type of backend metastore and METASTORE_NAME is the relative resource name of the metastore. If only the name of the metastore is specified (e.g. dpms1), project and location will be inferred from the project and location used to create the federation. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update a Dataproc Metastore federation with the name
my-metastore-federation in location us-central with two backends dpms1 and
dpms2, run:

    $ gcloud metastore federations update my-metastore-federation \
      --location=us-central1 \
      --update-backends=1=dpms:dpms1,2=dpms:projects/my-project/\
    locations/us-central1/services/dpms2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/federations/update)

---