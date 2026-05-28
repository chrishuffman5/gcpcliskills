# gcloud iam principal-access-boundary-policies

manage principal access boundary policies

### `gcloud iam principal-access-boundary-policies create`

Create PrincipalAccessBoundaryPolicy instance

Create PrincipalAccessBoundaryPolicy instance.

**Synopsis:**
```
gcloud iam principal-access-boundary-policies create
    (PRINCIPAL_ACCESS_BOUNDARY_POLICY
      : --location=LOCATION --organization=ORGANIZATION)
    [--annotations=[ANNOTATIONS,...]] [--async]
    [--display-name=DISPLAY_NAME] [--etag=ETAG]
    [[--details-rules=[description=DESCRIPTION],
      [effect=EFFECT],[resources=RESOURCES]
      : --details-enforcement-version=DETAILS_ENFORCEMENT_VERSION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PrincipalAccessBoundaryPolicy resource - Identifier. The resource name of
the principal access boundary policy.

The following format is supported:
organizations/{organization_id}/locations/{location}/principalAccessBoundaryPolicies/{policy_id}
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  PRINCIPAL_ACCESS_BOUNDARY_POLICY
     ID of the principalAccessBoundaryPolicy or fully qualified identifier
     for the principalAccessBoundaryPolicy.

     To set the principal_access_boundary_policy attribute:
     + provide the argument principal_access_boundary_policy on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the principalAccessBoundaryPolicy resource.

     To set the location attribute:
     + provide the argument principal_access_boundary_policy on the
       command line with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the principalAccessBoundaryPolicy resource.

     To set the organization attribute:
     + provide the argument principal_access_boundary_policy on the
       command line with a fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [ANNOTATIONS,...] |  | User defined annotations. See https://google.aip.dev/148#annotations for more details such as format and size limitations. KEY Sets KEY value. VALUE Sets VALUE value. Shorthand Example: --annotations=string=string JSON Example: --annotations='{"string": "string"}' File Example: --annotations=path_to_file.(yaml\|json) |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | The description of the principal access boundary policy. Must be less than or equal to 63 characters. |
| `--etag` | ETAG |  | The etag for the principal access boundary. If this is provided on update, it must match the server's etag. |


**Examples:**
```bash
To create a policy instance called my-policy, run:

    $ gcloud iam principal-access-boundary-policies create my-policy \
        --organization=123 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/principal-access-boundary-policies/create)

---
### `gcloud iam principal-access-boundary-policies delete`

Delete PrincipalAccessBoundaryPolicy instance

Delete PrincipalAccessBoundaryPolicy instance.

**Synopsis:**
```
gcloud iam principal-access-boundary-policies delete
    (PRINCIPAL_ACCESS_BOUNDARY_POLICY
      : --location=LOCATION --organization=ORGANIZATION) [--async]
    [--etag=ETAG] [--force] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PrincipalAccessBoundaryPolicy resource - The name of the principal access
boundary policy to delete.

Format:
organizations/{organization_id}/locations/{location}/principalAccessBoundaryPolicies/{principal_access_boundary_policy_id}
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  PRINCIPAL_ACCESS_BOUNDARY_POLICY
     ID of the principalAccessBoundaryPolicy or fully qualified identifier
     for the principalAccessBoundaryPolicy.

     To set the principal_access_boundary_policy attribute:
     + provide the argument principal_access_boundary_policy on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the principalAccessBoundaryPolicy resource.

     To set the location attribute:
     + provide the argument principal_access_boundary_policy on the
       command line with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the principalAccessBoundaryPolicy resource.

     To set the organization attribute:
     + provide the argument principal_access_boundary_policy on the
       command line with a fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | The etag of the principal access boundary policy. If this is provided, it must match the server's etag. |
| `--force` |  |  | If set to true, the request will force the deletion of the policy even if the policy is referenced in policy bindings. |


**Examples:**
```bash
To delete my-policy instance in organization 123, run:

    $ gcloud iam principal-access-boundary-policies delete my-policy \
        --organization=123 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/principal-access-boundary-policies/delete)

---
### `gcloud iam principal-access-boundary-policies describe`

Get PrincipalAccessBoundaryPolicy instance

Get PrincipalAccessBoundaryPolicy instance.

**Synopsis:**
```
gcloud iam principal-access-boundary-policies describe
    (PRINCIPAL_ACCESS_BOUNDARY_POLICY
      : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PrincipalAccessBoundaryPolicy resource - The name of the principal access
boundary policy to retrieve.

Format:
organizations/{organization_id}/locations/{location}/principalAccessBoundaryPolicies/{principal_access_boundary_policy_id}
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  PRINCIPAL_ACCESS_BOUNDARY_POLICY
     ID of the principalAccessBoundaryPolicy or fully qualified identifier
     for the principalAccessBoundaryPolicy.

     To set the principal_access_boundary_policy attribute:
     + provide the argument principal_access_boundary_policy on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the principalAccessBoundaryPolicy resource.

     To set the location attribute:
     + provide the argument principal_access_boundary_policy on the
       command line with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the principalAccessBoundaryPolicy resource.

     To set the organization attribute:
     + provide the argument principal_access_boundary_policy on the
       command line with a fully specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To get the details of a single policy my-policy in organization 123, run:

    $ gcloud iam principal-access-boundary-policies describe my-policy \
        --organization=123 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/principal-access-boundary-policies/describe)

---
### `gcloud iam principal-access-boundary-policies list`

List PrincipalAccessBoundaryPolicy instances

List PrincipalAccessBoundaryPolicy instances.

**Synopsis:**
```
gcloud iam principal-access-boundary-policies list
    (--location=LOCATION : --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ The organization id of the location resource. To set the organization attribute: + provide the argument --location on the command line with a fully specified name; + provide the argument --organization on the command line. |


**Examples:**
```bash
To list all policy instances in organization 123, run:

    $ gcloud iam principal-access-boundary-policies list \
        --organization=123 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/principal-access-boundary-policies/list)

---
### `gcloud iam principal-access-boundary-policies search-policy-bindings`

Search Principal Access Boundary Policy Bindings

Search all policy bindings that bind a specific policy if a user has
searchPolicyBindings permission on that policy.

**Synopsis:**
```
gcloud iam principal-access-boundary-policies search-policy-bindings
    (PRINCIPAL_ACCESS_BOUNDARY_POLICY
      : --location=LOCATION --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PrincipalAccessBoundaryPolicy resource - The name of the principal access
boundary policy. Format:
organizations/{organization_id}/locations/{location}/principalAccessBoundaryPolicies/{principal_access_boundary_policy_id}
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  PRINCIPAL_ACCESS_BOUNDARY_POLICY
     ID of the principalAccessBoundaryPolicy or fully qualified identifier
     for the principalAccessBoundaryPolicy.

     To set the principal_access_boundary_policy attribute:
     + provide the argument principal_access_boundary_policy on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the principalAccessBoundaryPolicy resource.

     To set the location attribute:
     + provide the argument principal_access_boundary_policy on the
       command line with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the principalAccessBoundaryPolicy resource.

     To set the organization attribute:
     + provide the argument principal_access_boundary_policy on the
       command line with a fully specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To search policy bindings associated with Principal Access Boundary Policy,
run:

$ gcloud iam principal-access-boundary-policies \        search-policy-bindings my-policy --organization=123 \
    --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/principal-access-boundary-policies/search-policy-bindings)

---
### `gcloud iam principal-access-boundary-policies update`

Update PrincipalAccessBoundaryPolicy instance

Update PrincipalAccessBoundaryPolicy instance.

**Synopsis:**
```
gcloud iam principal-access-boundary-policies update
    (PRINCIPAL_ACCESS_BOUNDARY_POLICY
      : --location=LOCATION --organization=ORGANIZATION) [--async]
    [--display-name=DISPLAY_NAME] [--etag=ETAG]
    [--annotations=[ANNOTATIONS,...]
      | --update-annotations=[UPDATE_ANNOTATIONS,...] --clear-annotations
      | --remove-annotations=REMOVE_ANNOTATIONS]
    [--clear-details
      --details-enforcement-version=DETAILS_ENFORCEMENT_VERSION
      --details-rules=[description=DESCRIPTION],
      [effect=EFFECT],[resources=RESOURCES]
      | --add-details-rules=[description=DESCRIPTION],
      [effect=EFFECT],[resources=RESOURCES] --clear-details-rules
      | --remove-details-rules=[description=DESCRIPTION],
      [effect=EFFECT],[resources=RESOURCES]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PrincipalAccessBoundaryPolicy resource - Identifier. The resource name of
the principal access boundary policy.

The following format is supported:
organizations/{organization_id}/locations/{location}/principalAccessBoundaryPolicies/{policy_id}
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  PRINCIPAL_ACCESS_BOUNDARY_POLICY
     ID of the principalAccessBoundaryPolicy or fully qualified identifier
     for the principalAccessBoundaryPolicy.

     To set the principal_access_boundary_policy attribute:
     + provide the argument principal_access_boundary_policy on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the principalAccessBoundaryPolicy resource.

     To set the location attribute:
     + provide the argument principal_access_boundary_policy on the
       command line with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the principalAccessBoundaryPolicy resource.

     To set the organization attribute:
     + provide the argument principal_access_boundary_policy on the
       command line with a fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | The description of the principal access boundary policy. Must be less than or equal to 63 characters. |
| `--etag` | ETAG |  | The etag for the principal access boundary. If this is provided on update, it must match the server's etag. |


**Examples:**
```bash
To update display name of my-policy in organization 123, run:

    $ gcloud iam principal-access-boundary-policies update my-policy \
        --organization=123 --location=global \
        --display-name=new-display-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/principal-access-boundary-policies/update)

---