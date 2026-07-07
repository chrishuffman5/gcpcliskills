# gcloud scc posture-deployments

manage Cloud Security Command Center posture deployments

### `gcloud scc posture-deployments create`

Create a Cloud Security Command Center posture deployment

Create a Cloud Security Command Center (SCC) posture deployment. First
argument is the parent of the posture deployment to be created. Second
argument is the name of the posture deployment to be created. It is
followed by details of the posture to be deployed and the target_resource
to be deployed on.

LRO operation ID is returned as the response of the command.

**Synopsis:**
```
gcloud scc posture-deployments create
    (POSTURE_DEPLOYMENT : --location=LOCATION --organization=ORGANIZATION)
    --posture-name=POSTURE_NAME --posture-revision-id=POSTURE_REVISION_ID
    --target-resource=TARGET_RESOURCE [--async] [--description=DESCRIPTION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Posture deployment resource - The name of the posture deployment to be
created. For example
organizations/<organizationID>/locations/<location>/postureDeployments/<postureDeploymentID>.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  POSTURE_DEPLOYMENT
     ID of the posture_deployment or fully qualified identifier for the
     posture_deployment.

     To set the posture_deployment attribute:
     + provide the argument posture_deployment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location where the resource exists (for example, global).

     To set the location attribute:
     + provide the argument posture_deployment on the command line with
       a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     ID of the organization which is the parent of the resource.

     To set the organization attribute:
     + provide the argument posture_deployment on the command line with
       a fully specified name;
     + provide the argument --organization on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--posture-name` | POSTURE_NAME |  | Posture that needs to be deployed. Format: organizations/<organizationID>/locations/<location>/postures/<postureID> |
| `--posture-revision-id` | POSTURE_REVISION_ID |  | Posture revision that needs to be deployed. |
| `--target-resource` | TARGET_RESOURCE |  | Name of the workload on which posture deployment is to be created. It could be an organization, folder or a project. Possible formats: \| organizations/<organizationID> \| folders/<folderID> \| projects/<projectID> The above mentioned IDs need to have numeric format. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | User-provided description of the posture deployment. |


**Examples:**
```bash
Create a posture deployment named posture-deployment-foo-1 within parent
organizations/123/locations/global on resource folders/456 (i.e. a
posture-deployment in organization 123, location global, with id
posture-deployment-foo-1, which deploys posture
organizations/123/locations/foo-posture with revision-id
foo-posture-revision-id on folders/456):

    $ gcloud scc posture-deployments create \
       organizations/123/locations/global/postureDeployments/\
    posture-deployment-foo-1 \
        --posture-name=organizations/123/locations/global/foo-posture \
        --posture-revision-id=foo-posture-revision-id \
        --target-resource=projects/456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/posture-deployments/create)

---
### `gcloud scc posture-deployments delete`

Delete a Cloud Security Command Center posture deployment

Delete a Cloud Security Command Center (SCC) posture deployment.

**Synopsis:**
```
gcloud scc posture-deployments delete
    (POSTURE_DEPLOYMENT : --location=LOCATION --organization=ORGANIZATION)
    [--async] [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Posture deployment resource - The posture deployment to delete. For
example
organizations/<organizationID>/locations/<location>/postureDeployments/<postureDeploymentID>.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  POSTURE_DEPLOYMENT
     ID of the posture_deployment or fully qualified identifier for the
     posture_deployment.

     To set the posture_deployment attribute:
     + provide the argument posture_deployment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location where the resource exists (for example, global).

     To set the location attribute:
     + provide the argument posture_deployment on the command line with
       a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     ID of the organization which is the parent of the resource.

     To set the organization attribute:
     + provide the argument posture_deployment on the command line with
       a fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | Etag is an optional flag. If the provided Etag doesn't match the server generated Etag, the delete operation won't proceed. |


**Examples:**
```bash
Delete the posture deployment named
organizations/123/locations/global/postureDeployments/posture-deployment-foo
(i.e. a posture deployment in organization 123, location global, with id
posture-deployment-foo):

    $ gcloud scc posture-deployments delete \
        organizations/123/locations/global/postureDeployments/\
    posture-deployment-foo

Delete the posture deployment named
organizations/123/locations/global/postureDeployments/posture-deployment-foo
(i.e. a posture deployment in organization 123, location global, with id
posture-deployment-foo) for the ETAG
ABcdO1Rf5clu7Yhlkwgelo7Vl4tiqd7Sy5iP5SdkSVU

    $ gcloud scc posture-deployments delete \
        organizations/123/locations/global/postureDeployments/\
    posture-deployment-foo \
        --etag=ABcdO1Rf5clu7Yhlkwgelo7Vl4tiqd7Sy5iI5SdkSVU
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/posture-deployments/delete)

---
### `gcloud scc posture-deployments describe`

Describe a Cloud Security Command Center posture deployment

Describe a Cloud Security Command Center (SCC) posture deployment.

**Synopsis:**
```
gcloud scc posture-deployments describe
    (POSTURE_DEPLOYMENT : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Posture deployment resource - The posture deployment to describe. For
example
organizations/<organizationID>/locations/<location>/postureDeployments/<postureDeploymentID>.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  POSTURE_DEPLOYMENT
     ID of the posture_deployment or fully qualified identifier for the
     posture_deployment.

     To set the posture_deployment attribute:
     + provide the argument posture_deployment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location where the resource exists (for example, global).

     To set the location attribute:
     + provide the argument posture_deployment on the command line with
       a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     ID of the organization which is the parent of the resource.

     To set the organization attribute:
     + provide the argument posture_deployment on the command line with
       a fully specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To describe posture deployment
organizations/123/locations/global/postureDeployments/posture-deployment-foo-1        (i.e. a posture deployment
    in organization `123`, location `global`, with ID `posture-deployment-foo-1`), run:

    $ gcloud scc posture-deployments describe \
    organizations/123/locations/global/postureDeployments/\
    posture-deployment-foo-1

    or, run:

    $ gcloud scc posture-deployments describe posture-deployment-foo-1 \
    --organization=123 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/posture-deployments/describe)

---
### `gcloud scc posture-deployments list`

List the details of the Cloud Security Command Center posture deployments

List the details of the Cloud Security Command Center (SCC) posture
deployments for the specified organization.

**Synopsis:**
```
gcloud scc posture-deployments list
    ([PARENT] --location=LOCATION --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Exactly one of these must be specified:

  [PARENT]
     Parent of Cloud Security Command Center posture deployments.
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
To list Cloud Security Command Center posture deployments for organization
123 in the global location, run:

    $ gcloud scc posture-deployments list \
        organizations/123/locations/global

    $ gcloud scc posture-deployments list --organization=123 \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/posture-deployments/list)

---
### `gcloud scc posture-deployments update`

Update the given Cloud Security Command Center posture deployment

Update a Cloud Security Command Center (SCC) posture deployment.

Fields specified in update-mask flag are updated. Updatable fields are
description and posture_name with posture_revision-id. The target_resource
for a posture deployment cannot be updated. The posture deployment to be
updated should be in ACTIVE State. An empty or "" update-mask implies that
posture-id and posture-revision-id are to be updated. If posture details of
posture deployment need to be updated, then the desired posture needs to be
in ACTIVE state. LRO operation ID is returned as the response of the
command.

**Synopsis:**
```
gcloud scc posture-deployments update
    (POSTURE_DEPLOYMENT : --location=LOCATION --organization=ORGANIZATION)
    [--async] [--description=DESCRIPTION] [--etag=ETAG]
    [--update-mask=UPDATE_MASK]
    [--posture-id=POSTURE_ID --posture-revision-id=POSTURE_REVISION_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Posture deployment resource - The posture deployment to update. For
example
organizations/<organizationID>/locations/<location>/postureDeployments/<postureDeploymentID>.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  POSTURE_DEPLOYMENT
     ID of the posture_deployment or fully qualified identifier for the
     posture_deployment.

     To set the posture_deployment attribute:
     + provide the argument posture_deployment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location where the resource exists (for example, global).

     To set the location attribute:
     + provide the argument posture_deployment on the command line with
       a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     ID of the organization which is the parent of the resource.

     To set the organization attribute:
     + provide the argument posture_deployment on the command line with
       a fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Updated description of posture deployment. |
| `--etag` | ETAG |  | Etag is an optional flag. If the provided Etag doesn't match the server generated Etag, the update operation won't proceed. |
| `--update-mask` | UPDATE_MASK |  | Comma-separated string containing list of fields to be updated. |
| `--posture-id` | POSTURE_ID |  | Relative name of the posture to be updated, like organizations/<organizationID>/locations/<location>/postures/<postureID>. |
| `--posture-revision-id` | POSTURE_REVISION_ID |  | Revision ID of the posture to be updated. |


**Examples:**
```bash
Update the description of the posture deployment named
foo-posture-deployment in the organization
organizations/123/locations/global:        $ gcloud scc posture-deployments update \
        organizations/123/locations/global/postureDeployments/\
    foo-posture-deployment --update-mask=description \
        --description="updated-description"

Update posture deployment named foo-posture-deployment with the posture
named foo-posture and revision_id abcdefgh in the organization
organizations/123/locations/global:        $ gcloud scc posture-deployments update \
        organizations/123/locations/global/postureDeployments/\
    foo-posture-deployment \
        --update-mask=posture_id,posture_revision-id \
        --posture-id=foo-posture --posture-revision-id=abcdefgh

    Update posture deployment named `foo-posture-deployment` with the posture named `foo-posture` and revision_id `abcdefgh` in the organization `organizations/123/locations/global`:
     $ gcloud scc posture-deployments update \
         organizations/123/locations/global/postureDeployments/\
     foo-posture-deployment --posture-id=foo-posture \
         --posture-revision-id=abcdefgh
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/posture-deployments/update)

---