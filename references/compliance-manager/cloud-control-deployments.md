# gcloud compliance-manager cloud-control-deployments

manage Cloud Control Deployment resources

### `gcloud compliance-manager cloud-control-deployments describe`

Get a cloud control deployment

Get the details for a specific cloud control deployment.

**Synopsis:**
```
gcloud compliance-manager cloud-control-deployments describe
    (CLOUD_CONTROL_DEPLOYMENT
      : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CloudControlDeployment resource - The name for the cloud control
deployment, in the format
organizations/{organization}/locations/{location}/cloudControlDeployments/{cloud_control_deployment_id}.
The only supported location is global. The arguments in this group can be
used to specify the attributes of this resource.

This must be specified.

  CLOUD_CONTROL_DEPLOYMENT
     ID of the cloudControlDeployment or fully qualified identifier for
     the cloudControlDeployment.

     To set the cloud_control_deployment attribute:
     + provide the argument cloud_control_deployment on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the cloudControlDeployment resource.

     To set the location attribute:
     + provide the argument cloud_control_deployment on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the cloudControlDeployment resource.

     To set the organization attribute:
     + provide the argument cloud_control_deployment on the command line
       with a fully specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To get the cloud control deployment my-cloud-control-deployment-id in
organization my-organization-id and location global, run:

    $ gcloud compliance-manager cloud-control-deployments describe \
        my-cloud-control-deployment-id \
        --organization=my-organization-id --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compliance-manager/cloud-control-deployments/describe)

---
### `gcloud compliance-manager cloud-control-deployments list`

List Cloud Control Deployments

List cloud control deployments for a given organization and location.

**Synopsis:**
```
gcloud compliance-manager cloud-control-deployments list
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
To list all cloud control deployments in organization my-organization-id
and location global, run:

    $ gcloud compliance-manager cloud-control-deployments list \
        --organization=my-organization-id --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compliance-manager/cloud-control-deployments/list)

---