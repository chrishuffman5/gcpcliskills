# gcloud iam policy-bindings

manage policy bindings

### `gcloud iam policy-bindings create`

Create PolicyBinding instance

Create PolicyBinding instance.

**Synopsis:**
```
gcloud iam policy-bindings create
    (POLICY_BINDING
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    --policy=POLICY --target-principal-set=TARGET_PRINCIPAL_SET
    [--annotations=[ANNOTATIONS,...]] [--async]
    [--display-name=DISPLAY_NAME] [--etag=ETAG] [--policy-kind=POLICY_KIND]
    [--condition-description=CONDITION_DESCRIPTION
      --condition-expression=CONDITION_EXPRESSION
      --condition-location=CONDITION_LOCATION
      --condition-title=CONDITION_TITLE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PolicyBinding resource - Identifier. The name of the policy binding, in
the format
{binding_parent/locations/{location}/policyBindings/{policy_binding_id}.
The binding parent is the closest Resource Manager resource (project,
folder, or organization) to the binding target.

Format:

 * projects/{project_id}/locations/{location}/policyBindings/{policy_binding_id}
 * projects/{project_number}/locations/{location}/policyBindings/{policy_binding_id}
 * folders/{folder_id}/locations/{location}/policyBindings/{policy_binding_id}
 * organizations/{organization_id}/locations/{location}/policyBindings/{policy_binding_id}
   The arguments in this group can be used to specify the attributes of
   this resource. (NOTE) Some attributes are not given arguments in this
   group but can be set in other ways.

To set the project attribute:
 * provide the argument policy_binding on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types: [iam.folders.locations.policyBindings,
   iam.organizations.locations.policyBindings,
   iam.projects.locations.policyBindings].

This must be specified.

  POLICY_BINDING
     ID of the policyBinding or fully qualified identifier for the
     policyBinding.

     To set the policy_binding attribute:
     + provide the argument policy_binding on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     The folder id of the policyBinding resource.

     To set the folder attribute:
     + provide the argument policy_binding on the command line with a
       fully specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [iam.folders.locations.policyBindings].

  --location=LOCATION
     The location id of the policyBinding resource.

     To set the location attribute:
     + provide the argument policy_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the policyBinding resource.

     To set the organization attribute:
     + provide the argument policy_binding on the command line with a
       fully specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [iam.organizations.locations.policyBindings].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--policy` | POLICY |  | The resource name of the policy to be bound. The binding parent and policy must belong to the same organization. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [ANNOTATIONS,...] |  | User-defined annotations. See https://google.aip.dev/148#annotations for more details such as format and size limitations. KEY Sets KEY value. VALUE Sets VALUE value. Shorthand Example: --annotations=string=string JSON Example: --annotations='{"string": "string"}' File Example: --annotations=path_to_file.(yaml\|json) |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | The description of the policy binding. Must be less than or equal to 63 characters. |
| `--etag` | ETAG |  | The etag for the policy binding. If this is provided on update, it must match the server's etag. |
| `--policy-kind` | POLICY_KIND |  | The kind of the policy to attach in this binding. This field must be one of the following: * Left empty (will be automatically set to the policy kind) * The input policy kind. POLICY_KIND must be (only one value is supported): principal-access-boundary Principal access boundary policy kind |


**Examples:**
```bash
To create a policy binding instance called my-binding that references a
principal access boundary policy run:

    $ gcloud iam policy-bindings create my-binding --organization=123 \
        --location=global \
        --policy=organizations/123/locations/global/\
    principalAccessBoundaryPolicies/my-policy \
        --target-principal-set=//cloudresourcemanager.googleapis.com/\
    organizations/123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/policy-bindings/create)

---
### `gcloud iam policy-bindings delete`

Delete PolicyBinding instance

Delete PolicyBinding instance.

**Synopsis:**
```
gcloud iam policy-bindings delete
    (POLICY_BINDING
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [--async] [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PolicyBinding resource - The name of the policy binding to delete.

Format:

 * projects/{project_id}/locations/{location}/policyBindings/{policy_binding_id}
 * projects/{project_number}/locations/{location}/policyBindings/{policy_binding_id}
 * folders/{folder_id}/locations/{location}/policyBindings/{policy_binding_id}
 * organizations/{organization_id}/locations/{location}/policyBindings/{policy_binding_id}
   The arguments in this group can be used to specify the attributes of
   this resource. (NOTE) Some attributes are not given arguments in this
   group but can be set in other ways.

To set the project attribute:
 * provide the argument policy_binding on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types: [iam.folders.locations.policyBindings,
   iam.organizations.locations.policyBindings,
   iam.projects.locations.policyBindings].

This must be specified.

  POLICY_BINDING
     ID of the policyBinding or fully qualified identifier for the
     policyBinding.

     To set the policy_binding attribute:
     + provide the argument policy_binding on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     The folder id of the policyBinding resource.

     To set the folder attribute:
     + provide the argument policy_binding on the command line with a
       fully specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [iam.folders.locations.policyBindings].

  --location=LOCATION
     The location id of the policyBinding resource.

     To set the location attribute:
     + provide the argument policy_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the policyBinding resource.

     To set the organization attribute:
     + provide the argument policy_binding on the command line with a
       fully specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [iam.organizations.locations.policyBindings].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | The etag of the policy binding. If this is provided, it must match the server's etag. |


**Examples:**
```bash
To delete my-binding instance in organization 123 run:

    $ gcloud iam policy-bindings delete my-binding --organization=123 \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/policy-bindings/delete)

---
### `gcloud iam policy-bindings describe`

Get PolicyBinding instance

Get PolicyBinding instance.

**Synopsis:**
```
gcloud iam policy-bindings describe
    (POLICY_BINDING
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PolicyBinding resource - The name of the policy binding to retrieve.

Format:

 * projects/{project_id}/locations/{location}/policyBindings/{policy_binding_id}
 * projects/{project_number}/locations/{location}/policyBindings/{policy_binding_id}
 * folders/{folder_id}/locations/{location}/policyBindings/{policy_binding_id}
 * organizations/{organization_id}/locations/{location}/policyBindings/{policy_binding_id}
   The arguments in this group can be used to specify the attributes of
   this resource. (NOTE) Some attributes are not given arguments in this
   group but can be set in other ways.

To set the project attribute:
 * provide the argument policy_binding on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types: [iam.folders.locations.policyBindings,
   iam.organizations.locations.policyBindings,
   iam.projects.locations.policyBindings].

This must be specified.

  POLICY_BINDING
     ID of the policyBinding or fully qualified identifier for the
     policyBinding.

     To set the policy_binding attribute:
     + provide the argument policy_binding on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     The folder id of the policyBinding resource.

     To set the folder attribute:
     + provide the argument policy_binding on the command line with a
       fully specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [iam.folders.locations.policyBindings].

  --location=LOCATION
     The location id of the policyBinding resource.

     To set the location attribute:
     + provide the argument policy_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the policyBinding resource.

     To set the organization attribute:
     + provide the argument policy_binding on the command line with a
       fully specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [iam.organizations.locations.policyBindings].
```

**Examples:**
```bash
To get the details of a single policy binding my-binding in organization
123 run:

    $ gcloud iam policy-bindings describe my-binding \
        --organization=123 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/policy-bindings/describe)

---
### `gcloud iam policy-bindings list`

List PolicyBinding instances

List PolicyBinding instances.

**Synopsis:**
```
gcloud iam policy-bindings list
    (--location=LOCATION : --folder=FOLDER --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--folder` | FOLDER |  | _[This must be specified.]_ The folder id of the location resource. To set the folder attribute: + provide the argument --location on the command line with a fully specified name; + provide the argument --folder on the command line. Must be specified for resource of type [iam.folders.locations]. |
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ The organization id of the location resource. To set the organization attribute: + provide the argument --location on the command line with a fully specified name; + provide the argument --organization on the command line. Must be specified for resource of type [iam.organizations.locations]. |


**Examples:**
```bash
To list all policy binding instances in project my-project run:

    $ gcloud iam policy-bindings list --project=my-project \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/policy-bindings/list)

---
### `gcloud iam policy-bindings search-target-policy-bindings`

Search policy bindings by target

Search policy bindings by target.

**Synopsis:**
```
gcloud iam policy-bindings search-target-policy-bindings --target=TARGET
    (--location=LOCATION : --folder=FOLDER --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target` | TARGET |  | The target resource, which is bound to the policy in the binding. Format: * //iam.googleapis.com/locations/global/workforcePools/POOL_ID * //iam.googleapis.com/projects/PROJECT_NUMBER/locations/global/workloadIdentityPools/POOL_ID * //iam.googleapis.com/locations/global/workspace/WORKSPACE_ID * //cloudresourcemanager.googleapis.com/projects/{project_number} * //cloudresourcemanager.googleapis.com/folders/{folder_id} * //cloudresourcemanager.googleapis.com/organizations/{organization_id} |


**Examples:**
```bash
To search for policy bindings with target, run:

    $ gcloud iam policy-bindings search-target-policy-bindings \
        --organization=123 --location=global \
        --target=//cloudresourcemanager.googleapis.com/organizations/123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/policy-bindings/search-target-policy-bindings)

---
### `gcloud iam policy-bindings update`

Update PolicyBinding instance

Update PolicyBinding instance.

**Synopsis:**
```
gcloud iam policy-bindings update
    (POLICY_BINDING
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [--async] [--display-name=DISPLAY_NAME] [--etag=ETAG]
    [--annotations=[ANNOTATIONS,...]
      | --update-annotations=[UPDATE_ANNOTATIONS,...] --clear-annotations
      | --remove-annotations=REMOVE_ANNOTATIONS]
    [--clear-condition --condition-description=CONDITION_DESCRIPTION
      --condition-expression=CONDITION_EXPRESSION
      --condition-location=CONDITION_LOCATION
      --condition-title=CONDITION_TITLE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PolicyBinding resource - Identifier. The name of the policy binding, in
the format
{binding_parent/locations/{location}/policyBindings/{policy_binding_id}.
The binding parent is the closest Resource Manager resource (project,
folder, or organization) to the binding target.

Format:

 * projects/{project_id}/locations/{location}/policyBindings/{policy_binding_id}
 * projects/{project_number}/locations/{location}/policyBindings/{policy_binding_id}
 * folders/{folder_id}/locations/{location}/policyBindings/{policy_binding_id}
 * organizations/{organization_id}/locations/{location}/policyBindings/{policy_binding_id}
   The arguments in this group can be used to specify the attributes of
   this resource. (NOTE) Some attributes are not given arguments in this
   group but can be set in other ways.

To set the project attribute:
 * provide the argument policy_binding on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types: [iam.folders.locations.policyBindings,
   iam.organizations.locations.policyBindings,
   iam.projects.locations.policyBindings].

This must be specified.

  POLICY_BINDING
     ID of the policyBinding or fully qualified identifier for the
     policyBinding.

     To set the policy_binding attribute:
     + provide the argument policy_binding on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     The folder id of the policyBinding resource.

     To set the folder attribute:
     + provide the argument policy_binding on the command line with a
       fully specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [iam.folders.locations.policyBindings].

  --location=LOCATION
     The location id of the policyBinding resource.

     To set the location attribute:
     + provide the argument policy_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the policyBinding resource.

     To set the organization attribute:
     + provide the argument policy_binding on the command line with a
       fully specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [iam.organizations.locations.policyBindings].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | The description of the policy binding. Must be less than or equal to 63 characters. |
| `--etag` | ETAG |  | The etag for the policy binding. If this is provided on update, it must match the server's etag. |


**Examples:**
```bash
To update display name of my-binding in organization 123 run:

    $ gcloud iam policy-bindings update my-binding --organization=123 \
        --location=global --display-name=new-display-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/policy-bindings/update)

---