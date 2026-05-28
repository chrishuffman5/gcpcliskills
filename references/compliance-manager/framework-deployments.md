# gcloud compliance-manager framework-deployments

manage Framework Deployment resources

### `gcloud compliance-manager framework-deployments create`

Create a framework deployment

Create a framework deployment for a given organization and location.

**Synopsis:**
```
gcloud compliance-manager framework-deployments create
    (FRAMEWORK_DEPLOYMENT
      : --location=LOCATION --organization=ORGANIZATION)
    --cloud-control-metadata=[cloudControlDetails=CLOUDCONTROLDETAILS],
      [enforcementMode=ENFORCEMENTMODE]
    (--framework=FRAMEWORK
      : --framework-major-revision-id=FRAMEWORK_MAJOR_REVISION_ID)
    (--target-resource-config-existing=TARGET_RESOURCE_CONFIG_EXISTING
      | --target-resource-creation-config-folder-display-name=TARGET_RESOURCE_CREATION_CONFIG_FOLDER_DISPLAY_NAME --target-resource-creation-config-folder-parent=TARGET_RESOURCE_CREATION_CONFIG_FOLDER_PARENT | --target-resource-creation-config-project-billing-account-id=TARGET_RESOURCE_CREATION_CONFIG_PROJECT_BILLING_ACCOUNT_ID --target-resource-creation-config-project-display-name=TARGET_RESOURCE_CREATION_CONFIG_PROJECT_DISPLAY_NAME --target-resource-creation-config-project-parent=TARGET_RESOURCE_CREATION_CONFIG_PROJECT_PARENT)
    [--async] [--description=DESCRIPTION] [--etag=ETAG]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FrameworkDeployment resource - Identifier. The name of the framework
deployment, in the format
organizations/{organization}/locations/{location}/frameworkDeployments/{framework_deployment_id}.
The only supported location is global. The arguments in this group can be
used to specify the attributes of this resource.

This must be specified.

  FRAMEWORK_DEPLOYMENT
     ID of the frameworkDeployment or fully qualified identifier for the
     frameworkDeployment.

     To set the framework_deployment attribute:
     + provide the argument framework_deployment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the frameworkDeployment resource.

     To set the location attribute:
     + provide the argument framework_deployment on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the frameworkDeployment resource.

     To set the organization attribute:
     + provide the argument framework_deployment on the command line
       with a fully specified name;
     + provide the argument --organization on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cloud-control-metadata` | [cloudControlDetails=CLOUDCONTROLDETAILS],[enforcementMode=ENFORCEMENTMODE] |  | Required, The deployment mode and parameters for each of the cloud controls in the framework. Every cloud control in the framework includes metadata. cloudControlDetails The cloud control name and parameters. majorRevisionId The major version of the cloud control. name The name of the cloud control, in the format organizations/{organization}/locations/{location}/cloudControls/{cloud-control}. The only supported location is global. parameters Parameters are key-value pairs that let you provide your custom location requirements, environment requirements, or other settings that are relevant to the cloud control. An example parameter is {"name": "location","value": "us-west-1"}. name The name or key of the parameter. enforcementMode The enforcement mode of the cloud control. Shorthand Example: --cloud-control-metadata=cloudControlDetails={majorRevisionId=int,name=string,parameters=[{name=string}]},enforcementMode=string --cloud-control-metadata=cloudControlDetails={majorRevisionId=int,name=string,parameters=[{name=string}]},enforcementMode=string JSON Example: --cloud-control-metadata='[{"cloudControlDetails": {"majorRevisionId": int, "name": "string", "parameters": [{"name": "string"}]}, "enforcementMode": "string"}]' File Example: --cloud-control-metadata=path_to_file.(yaml\|json) |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A user-provided description of the framework deployment. |
| `--etag` | ETAG |  | To prevent concurrent updates from overwriting each other, always provide the etag when you update a framework deployment. You can also provide the etag when you delete a framework deployment, to help ensure that you're deleting the intended version of the framework deployment. |


**Examples:**
```bash
To create a framework deployment my-framework-deployment-id in organization
my-organization-id and location global, targeting folders/my-folder-id and
using framework my-framework-name, run:

    $ gcloud compliance-manager framework-deployments create \
        my-framework-deployment-id --organization=my-organization-id \
        --location=global \
        --target-resource-config-existing=folders/my-folder-id \
        --framework='organizations/my-organization-id/locations/global/f\
    rameworks/my-framework-name' --framework-major-revision-id='1' \
        --cloud-control-metadata='[{"cloudControlDetails": {"name":
     "organizations/my-organization-id/locations/global/cloudControls/my\
    -control-1", "majorRevisionId": "1", "parameters": []},
     "enforcementMode": "DETECTIVE"}]'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compliance-manager/framework-deployments/create)

---
### `gcloud compliance-manager framework-deployments delete`

Delete a framework deployment

Delete a specific framework deployment.

**Synopsis:**
```
gcloud compliance-manager framework-deployments delete
    (FRAMEWORK_DEPLOYMENT
      : --location=LOCATION --organization=ORGANIZATION) [--async]
    [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FrameworkDeployment resource - The name of the framework deployment that
you want to delete, in the format
organizations/{organization}/locations/{location}/frameworkDeployments/{framework_deployment_id}.
The only supported location is global. The arguments in this group can be
used to specify the attributes of this resource.

This must be specified.

  FRAMEWORK_DEPLOYMENT
     ID of the frameworkDeployment or fully qualified identifier for the
     frameworkDeployment.

     To set the framework_deployment attribute:
     + provide the argument framework_deployment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the frameworkDeployment resource.

     To set the location attribute:
     + provide the argument framework_deployment on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the frameworkDeployment resource.

     To set the organization attribute:
     + provide the argument framework_deployment on the command line
       with a fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | An opaque identifier for the current version of the resource. If you provide this value, then it must match the existing value. If the values don't match, then the request fails with an [ABORTED][google.rpc.Code.ABORTED] error. If you omit this value, then the resource is deleted regardless of its current etag value. |


**Examples:**
```bash
To delete the framework deployment my-framework-deployment-id in
organization my-organization-id and location global, run:

    $ gcloud compliance-manager framework-deployments delete \
        my-framework-deployment-id --organization=my-organization-id \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compliance-manager/framework-deployments/delete)

---
### `gcloud compliance-manager framework-deployments describe`

Get a framework deployment

Get the details for a specific framework deployment.

**Synopsis:**
```
gcloud compliance-manager framework-deployments describe
    (FRAMEWORK_DEPLOYMENT
      : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FrameworkDeployment resource - The name of the framework deployment, in
the format
organizations/{organization}/locations/{location}/frameworkDeployments/{framework_deployment_id}.
The only supported location is global. The arguments in this group can be
used to specify the attributes of this resource.

This must be specified.

  FRAMEWORK_DEPLOYMENT
     ID of the frameworkDeployment or fully qualified identifier for the
     frameworkDeployment.

     To set the framework_deployment attribute:
     + provide the argument framework_deployment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the frameworkDeployment resource.

     To set the location attribute:
     + provide the argument framework_deployment on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the frameworkDeployment resource.

     To set the organization attribute:
     + provide the argument framework_deployment on the command line
       with a fully specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To get the framework deployment my-framework-deployment-id in organization
my-organization-id and location global, run:

    $ gcloud compliance-manager framework-deployments describe \
        my-framework-deployment-id --organization=my-organization-id \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compliance-manager/framework-deployments/describe)

---
### `gcloud compliance-manager framework-deployments list`

List framework deployments

List all framework deployments for a given organization and location.

**Synopsis:**
```
gcloud compliance-manager framework-deployments list
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
To list all framework deployments in organization my-organization-id and
location global, run:

    $ gcloud compliance-manager framework-deployments list \
        --organization=my-organization-id --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compliance-manager/framework-deployments/list)

---