# gcloud data-catalog entry-groups

manage entry groups in Data Catalog

### `gcloud data-catalog entry-groups add-iam-policy-binding`

Add an IAM policy binding to a Data Catalog entry group

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
entry-groups instead.

Add an IAM policy binding to a Data Catalog entry group.

**Synopsis:**
```
gcloud data-catalog entry-groups add-iam-policy-binding
    (ENTRY_GROUP : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry group resource - Entry group for which to add an IAM policy binding.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument entry_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY_GROUP
     ID of the entry group or fully qualified identifier for the entry
     group.

     To set the entry_group attribute:
     + provide the argument entry_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the entry group.

     To set the location attribute:
     + provide the argument entry_group on the command line with a fully
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
'test-user@gmail.com' with entry group 'group1' and location 'us-central1',
run:

    $ gcloud data-catalog entry-groups add-iam-policy-binding group1 \
        --location='us-central1' --member='user:test-user@gmail.com' \
        --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entry-groups/add-iam-policy-binding)

---
### `gcloud data-catalog entry-groups create`

Create a Data Catalog entry group

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
entry-groups instead.

Create a Data Catalog entry group.

**Synopsis:**
```
gcloud data-catalog entry-groups create (ENTRY_GROUP : --location=LOCATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry group resource - Entry group to create. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument entry_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY_GROUP
     ID of the entry group or fully qualified identifier for the entry
     group.

     To set the entry_group attribute:
     + provide the argument entry_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the entry group.

     To set the location attribute:
     + provide the argument entry_group on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the entry group. |
| `--display-name` | DISPLAY_NAME |  | Human-readable name of the entry group. |


**Examples:**
```bash
To create an entry group for some data, run:

    $ gcloud data-catalog entry-groups create group1 \
        --location=us-central1 \
        --display-name="analytics data - jan 2011" \
        --description="Entries related to January 2011 analytics data."
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entry-groups/create)

---
### `gcloud data-catalog entry-groups delete`

Delete a Data Catalog entry group

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
entry-groups instead.

Delete a Data Catalog entry group.

**Synopsis:**
```
gcloud data-catalog entry-groups delete (ENTRY_GROUP : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry group resource - Entry group to delete. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument entry_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY_GROUP
     ID of the entry group or fully qualified identifier for the entry
     group.

     To set the entry_group attribute:
     + provide the argument entry_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the entry group.

     To set the location attribute:
     + provide the argument entry_group on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete an entry group for some data, run:

    $ gcloud data-catalog entry-groups delete group1 \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entry-groups/delete)

---
### `gcloud data-catalog entry-groups describe`

Describe a Data Catalog entry group

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
entry-groups instead.

Describe a Data Catalog entry group.

**Synopsis:**
```
gcloud data-catalog entry-groups describe
    (ENTRY_GROUP : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry group resource - Entry group to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument entry_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY_GROUP
     ID of the entry group or fully qualified identifier for the entry
     group.

     To set the entry_group attribute:
     + provide the argument entry_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the entry group.

     To set the location attribute:
     + provide the argument entry_group on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe an entry group for some data, run:

    $ gcloud data-catalog entry-groups describe group1 \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entry-groups/describe)

---
### `gcloud data-catalog entry-groups get-iam-policy`

Get the IAM policy for a Data Catalog entry group

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
entry-groups instead.

gcloud data-catalog entry-groups get-iam-policy displays the IAM policy
associated with a Data Catalog entry group. If formatted as JSON, the
output can be edited and used as a policy file for set-iam-policy. The
output includes an "etag" field identifying the version emitted and
allowing detection of concurrent policy updates; see $ gcloud data-catalog
entry-groups set-iam-policy for additional details.

**Synopsis:**
```
gcloud data-catalog entry-groups get-iam-policy
    (ENTRY_GROUP : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry group resource - Entry group for which to display the IAM policy.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument entry_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY_GROUP
     ID of the entry group or fully qualified identifier for the entry
     group.

     To set the entry_group attribute:
     + provide the argument entry_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the entry group.

     To set the location attribute:
     + provide the argument entry_group on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To print the IAM policy for entry group 'group1' in 'us-central1', run:

    $ gcloud data-catalog entry-groups get-iam-policy \
        --location=us-central1 group1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entry-groups/get-iam-policy)

---
### `gcloud data-catalog entry-groups list`

List all entry groups in a Data Catalog location

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
entry-groups instead.

List all entries in a Data Catalog location.

**Synopsis:**
```
gcloud data-catalog entry-groups list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all entry groups in us-central1, run:

    $ gcloud data-catalog entry-groups list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entry-groups/list)

---
### `gcloud data-catalog entry-groups remove-iam-policy-binding`

Remove an IAM policy binding from a Data Catalog entry group

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
entry-groups instead.

Remove an IAM policy binding from a Data Catalog entry group.

**Synopsis:**
```
gcloud data-catalog entry-groups remove-iam-policy-binding
    (ENTRY_GROUP : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry group resource - Entry group from which to remove the IAM policy
binding. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument entry_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY_GROUP
     ID of the entry group or fully qualified identifier for the entry
     group.

     To set the entry_group attribute:
     + provide the argument entry_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the entry group.

     To set the location attribute:
     + provide the argument entry_group on the command line with a fully
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
'test-user@gmail.com' on entry group 'group1' with location 'us-central1',
run:

    $ gcloud data-catalog entry-groups remove-iam-policy-binding \
        --location=us-central1 group1 \
        --member='user:test-user@gmail.com' --role='roles/editor'

To remove an IAM policy binding for the role of 'roles/editor' from all
authenticated users on entry group 'group1' with location 'us-central1',
run:

    $ gcloud data-catalog entry-groups remove-iam-policy-binding \
        --location=us-central1 group1 --member='allAuthenticatedUsers' \
        --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entry-groups/remove-iam-policy-binding)

---
### `gcloud data-catalog entry-groups set-iam-policy`

Set the IAM policy for a Data Catalog entry group

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
entry-groups instead.

Set the IAM policy for the given Data Catalog entry group as defined in a
JSON or YAML file.

**Synopsis:**
```
gcloud data-catalog entry-groups set-iam-policy
    (ENTRY_GROUP : --location=LOCATION) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry group resource - Entry group for which to set the IAM policy. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument entry_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY_GROUP
     ID of the entry group or fully qualified identifier for the entry
     group.

     To set the entry_group attribute:
     + provide the argument entry_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the entry group.

     To set the location attribute:
     + provide the argument entry_group on the command line with a fully
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
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the entry group 'group1' with location
'us-central1':

    $ gcloud data-catalog entry-groups set-iam-policy group1 \
        --location=us-central1 policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entry-groups/set-iam-policy)

---
### `gcloud data-catalog entry-groups update`

Update a Data Catalog entry group

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
entry-groups instead.

Update a Data Catalog entry group.

**Synopsis:**
```
gcloud data-catalog entry-groups update (ENTRY_GROUP : --location=LOCATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry group resource - Entry group to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument entry_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY_GROUP
     ID of the entry group or fully qualified identifier for the entry
     group.

     To set the entry_group attribute:
     + provide the argument entry_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the entry group.

     To set the location attribute:
     + provide the argument entry_group on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the entry group. |
| `--display-name` | DISPLAY_NAME |  | Human-readable name of the entry group. |


**Examples:**
```bash
To update the description of entry group 'group1' , run:

    $ gcloud data-catalog entry-groups update group1 \
        --location=us-central1 --description="new description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entry-groups/update)

---