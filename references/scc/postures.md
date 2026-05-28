# gcloud scc postures

manage Cloud Security Command Center postures

### `gcloud scc postures create`

Create a Cloud Security Command Center posture

Create a Cloud Security Command Center (SCC) posture. First argument
consists of the parent and name of the posture to be created. The posture
details are provided in YAML file. The file path is mentioned in
--posture-from-file flag.

Created posture is returned as the response of the command. LRO operation
ID is printed as the standard output.

**Synopsis:**
```
gcloud scc postures create
    (POSTURE : --location=LOCATION --organization=ORGANIZATION)
    --posture-from-file=PATH_TO_FILE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Posture resource - The name of the posture to be created. For example
organizations/<organizationID>/locations/<location>/postures/<postureID>.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  POSTURE
     ID of the posture or fully qualified identifier for the posture.

     To set the posture attribute:
     + provide the argument posture on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location where the resource exists (for example, global).

     To set the location attribute:
     + provide the argument posture on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     ID of the organization which is the parent of the resource.

     To set the organization attribute:
     + provide the argument posture on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--posture-from-file` | PATH_TO_FILE |  | YAML file containing the body of the posture to be created. Use a full or relative path to a local file containing the value of posture. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
Create a posture named posture-foo-1 within parent
organizations/123/locations/global(i.e. a posture in organization 123,
location global, with ID posture-foo-1):

    $ gcloud scc postures create \
       organizations/123/locations/global/postures/posture-foo-1 \
       --posture-from-file=posture.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/postures/create)

---
### `gcloud scc postures delete`

Delete a Cloud Security Command Center posture

Delete a Cloud Security Command Center (SCC) posture.

Posture with all its revisions is deleted. Deletion won't be allowed in
case any of the versions of the posture is deployed on a workload. ETAG can
be provided as an optional flag.

**Synopsis:**
```
gcloud scc postures delete
    (POSTURE : --location=LOCATION --organization=ORGANIZATION) [--async]
    [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Posture resource - The name of the posture to be deleted. For example
organizations/<organizationID>/locations/<location>/postures/<postureID>.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  POSTURE
     ID of the posture or fully qualified identifier for the posture.

     To set the posture attribute:
     + provide the argument posture on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location where the resource exists (for example, global).

     To set the location attribute:
     + provide the argument posture on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     ID of the organization which is the parent of the resource.

     To set the organization attribute:
     + provide the argument posture on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | Etag is an optional flag. If the provided Etag doesn't match the server generated Etag, the delete operation won't proceed. |


**Examples:**
```bash
Delete the posture named
organizations/123/locations/global/postures/posture-foo-1 (i.e. a posture
in organization 123, location global, with id posture-foo-1):

    $ gcloud scc postures delete \
        organizations/123/locations/global/postures/posture-foo-1

Delete the posture named
organizations/123/locations/global/postures/posture-foo-1 (i.e. a posture
in organization 123, location global, with id posture-foo-1) for the ETAG
ABcdO1Rf5clu7Yhlkwgelo7Vl4tiqd7Sy5iP5SdkSVU

    $ gcloud scc postures delete \
        organizations/123/locations/global/postures/posture-foo-1 \
        --etag=ABcdO1Rf5clu7Yhlkwgelo7Vl4tiqd7Sy5iI5SdkSVU
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/postures/delete)

---
### `gcloud scc postures describe`

Describe a Cloud Security Command Center posture

Describe a Cloud Security Command Center (SCC) posture.

By default, the latest updated revision of the posture is described. Users
must provide revision ID to describe a specific revision.

**Synopsis:**
```
gcloud scc postures describe
    (POSTURE : --location=LOCATION --organization=ORGANIZATION)
    [--revision-id=REVISION_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Posture resource - The posture to be described. For example
organizations/<organizationID>/locations/<location>/postures/<postureID>.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  POSTURE
     ID of the posture or fully qualified identifier for the posture.

     To set the posture attribute:
     + provide the argument posture on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location where the resource exists (for example, global).

     To set the location attribute:
     + provide the argument posture on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     ID of the organization which is the parent of the resource.

     To set the organization attribute:
     + provide the argument posture on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--revision-id` | REVISION_ID |  | ID of the specific posture revision to described. If not specified, latest revision is described. |


**Examples:**
```bash
Describe the latest updated revision of a posture named
organizations/123/locations/global/postures/posture-foo-1 (i.e. a posture
in organization 123, location global, with id posture-foo-1):

    $ gcloud scc postures describe \
        organizations/123/locations/global/postures/posture-foo-1

Describe a specific revision abcdefg of posture named
organizations/123/locations/global/postures/posture-foo-1:

    $ gcloud scc postures describe \
        organizations/123/locations/global/postures/posture-foo-1 \
        --revision-id=abcdefg
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/postures/describe)

---
### `gcloud scc postures extract`

Extract a Cloud Security Command Center posture from a workload

Extract a Cloud Security Command Center (SCC) posture from a workload.
First argument is the parent and name of the posture to be created. The
workload from where the organization policies need to be extracted is
provided via '--workload' flag.

Extracted posture is returned as the response of the command. LRO operation
ID is printed as the standard output.

**Synopsis:**
```
gcloud scc postures extract
    (POSTURE : --location=LOCATION --organization=ORGANIZATION)
    --workload=WORKLOAD [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Posture resource - The name of the posture to be created. For example
organizations/<organizationID>/locations/<location>/postures/<postureID>.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  POSTURE
     ID of the posture or fully qualified identifier for the posture.

     To set the posture attribute:
     + provide the argument posture on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location where the resource exists (for example, global).

     To set the location attribute:
     + provide the argument posture on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     ID of the organization which is the parent of the resource.

     To set the organization attribute:
     + provide the argument posture on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--workload` | WORKLOAD |  | Workload from where policies has to be extracted into a posture. It can be in one of the following formats: projects/projectNumber, folders/folderNumber, organizations/organizationNumber. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
Extract a posture named posture-foo-1 within parent
organizations/123/locations/global(i.e. a posture in organization 123,
location global, with id posture-foo-1) from workload projects/456:

    $ gcloud scc postures extract \
       organizations/123/locations/global/postures/posture-foo-1 \
       --workload=projects/456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/postures/extract)

---
### `gcloud scc postures list`

Lists all the Cloud Security Command Center postures for an organization

Lists all the Cloud Security Command Center postures for an organization.

**Synopsis:**
```
gcloud scc postures list
    ([PARENT] --location=LOCATION --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Exactly one of these must be specified:

  [PARENT]
     Parent the Cloud Security Command Center postures belongs to.
     Formatted as organizations/<organizationID>/locations/<location>.

  Specify organization and location using flags.

    --location=LOCATION
       When data residency controls are enabled, this attribute specifies
       the location in which the resource is located and applicable.

       This flag argument must be specified if any of the other arguments
       in this group are specified.

    --organization=ORGANIZATION
       The organization ID (e.g., 123) that contains the resource.

       This flag argument must be specified if any of the other arguments
       in this group are specified.
```

**Examples:**
```bash
To list all the Cloud Security Command Center postures for an organization
123 and in the global location, run:

    $ gcloud scc postures list organizations/123/locations/global

    $ gcloud scc postures list --organization=123 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/postures/list)

---
### `gcloud scc postures list-revisions`

List the revisions of a Cloud Security Command Center posture

List the revisions of a Cloud Security Command Center (SCC) posture.

**Synopsis:**
```
gcloud scc postures list-revisions
    (POSTURE : --location=LOCATION --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Posture resource - The posture whose revisions are to be listed. For
example
organizations/<organizationID>/locations/<location>/postures/<postureID>.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  POSTURE
     ID of the posture or fully qualified identifier for the posture.

     To set the posture attribute:
     + provide the argument posture on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location where the resource exists (for example, global).

     To set the location attribute:
     + provide the argument posture on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     ID of the organization which is the parent of the resource.

     To set the organization attribute:
     + provide the argument posture on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To list Cloud Security Command Center posture revisions for posture
organizations/123/locations/global/postures/posture123 , run:

    $ gcloud scc postures list-revisions \
        organizations/123/locations/global/postures/posture123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/postures/list-revisions)

---
### `gcloud scc postures update`

Update the given Cloud Security Command Center posture

Update a Cloud Security Command Center (SCC) posture.

Fields specified in update-mask flag are updated. Updatable fields are
state, description and policy_sets. State of the posture can't be updated
along with update of other fields. An empty or "" as field mask will result
in update of policy_sets and description. In case of the update of
policy_sets, the value mentioned in the update posture request overwrites
the exisiting value of policy_sets.

Valid state transitions are: a) ACTIVE to DRAFT b) ACTIVE to DEPRECATED c)
DRAFT to ACTIVE d) DEPRECATED to ACTIVE

The update operation will result in the update of the revision-id specified
in the request, unless the posture revision is currently deployed on a
workload. A new revision is created for an already deployed posture
revision.

**Synopsis:**
```
gcloud scc postures update
    (POSTURE : --location=LOCATION --organization=ORGANIZATION)
    --posture-from-file=PATH_TO_FILE --revision-id=REVISION_ID [--async]
    [--update-mask=UPDATE_MASK] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Posture resource - Arguments and flags that specify the Posture instance
to be updated. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  POSTURE
     ID of the posture or fully qualified identifier for the posture.

     To set the posture attribute:
     + provide the argument posture on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location where the resource exists (for example, global).

     To set the location attribute:
     + provide the argument posture on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     ID of the organization which is the parent of the resource.

     To set the organization attribute:
     + provide the argument posture on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--posture-from-file` | PATH_TO_FILE |  | Path of the file containing the details of the field to be updated. Contents include the name of the posture to be updated and value of the fields to be updated. Use a full or relative path to a local file containing the value of posture. |
| `--revision-id` | REVISION_ID |  | Revision ID of the posture to be updated. The same revision ID will be updated in case the posture revision is not deployed on any workload. A new revision will be created for a deployed posture. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--update-mask` | UPDATE_MASK |  | Comma separated string containing list of fields to be updated. |


**Examples:**
```bash
Update the revision-id abcdefgh of the posture named foo-posture in the
organization organizations/123/locations/global: Change State to ACTIVE.        $ gcloud scc postures update \
        organizations/123/locations/global/postures/foo-posture \
        --posture-from-file=update_posture.yaml --revision-id=abcdefgh \
        update_mask=state

    Contents of update_posture.yaml are |
        name: organizations/123/locations/global/postures/foo-posture
        state: ACTIVE

Update the revision-id abcdefgh of the posture named foo-posture in the
organization organizations/123/locations/global: Change description and
policy_sets to the values mentioned in update_posture.yaml        $ gcloud scc postures update \
        organizations/123/locations/global/postures/foo-posture \
        --posture-from-file=update_posture.yaml --revision-id=abcdefgh \
        update_mask=description,policy_sets

    Contents of update_posture.yaml are |
        name: organizations/123/locations/global/postures/foo-posture
        description: updated description
        policy_sets:
        - policy_set_id: newPolicySet1
          policies:
            - policy_id: newPolicy
              constraint:
                org_policy_canned_constraint:
                  canned_constraint_id: storage.uniformBucketLevelAccess
                  policy_rules:
                    enforce: false
        - policy_set_id: PolicySet2
          policies:
            - policy_id: Policy3
              constraint:
                org_policy_custom_constraint:
                  custom_constraint:
                    name: organizations/9454078371/customConstraints/custom.newConstraint
                    resource_types: container.$$UNIVERSE_DOMAIN$$/NodePool
                    method_types: UPDATE
                    condition: resource.management.autoUpgrade == false
                    action_type: ALLOW
                  policy_rules:
                    enforce: true
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/postures/update)

---