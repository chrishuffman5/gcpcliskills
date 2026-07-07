# gcloud network-security mirroring-deployments

manage Mirroring Deployment resources

### `gcloud network-security mirroring-deployments create`

Create a Mirroring Deployment

Create a mirroring deployment. Successful creation of a deployment results
in a deployment in ACTIVE state. Check the progress of deployment creation
by using gcloud network-security mirroring-deployments list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security mirroring-deployments create
    (MIRRORING_DEPLOYMENT : --location=LOCATION)
    (--forwarding-rule=FORWARDING_RULE
      : --forwarding-rule-location=FORWARDING_RULE_LOCATION)
    (--mirroring-deployment-group=MIRRORING_DEPLOYMENT_GROUP
      : --mirroring-deployment-group-location=MIRRORING_DEPLOYMENT_GROUP_LOCATION)
    [--async] [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--max-wait=MAX_WAIT; default="20m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Mirroring deployment resource - Mirroring Deployment. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument MIRRORING_DEPLOYMENT on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIRRORING_DEPLOYMENT
     ID of the mirroring deployment or fully qualified identifier for the
     mirroring deployment.

     To set the deployment-id attribute:
     + provide the argument MIRRORING_DEPLOYMENT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the mirroring deployment.

     To set the location attribute:
     + provide the argument MIRRORING_DEPLOYMENT on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--forwarding-rule` | FORWARDING_RULE |  | _[This must be specified.]_ ID of the forwardingRule or fully qualified identifier for the forwardingRule. To set the forwarding-rule-id attribute: + provide the argument --forwarding-rule on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--forwarding-rule-location` | FORWARDING_RULE_LOCATION |  | _[This must be specified.]_ The Cloud region for the forwardingRule. To set the forwarding-rule-location attribute: + provide the argument --forwarding-rule on the command line with a fully specified name; + provide the argument --forwarding-rule-location on the command line. |
| `--mirroring-deployment-group` | MIRRORING_DEPLOYMENT_GROUP |  | _[This must be specified.]_ ID of the mirroring deployment group or fully qualified identifier for the mirroring deployment group. To set the id attribute: + provide the argument --mirroring-deployment-group on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--mirroring-deployment-group-location` | MIRRORING_DEPLOYMENT_GROUP_LOCATION |  | _[This must be specified.]_ Location of the mirroring deployment group. To set the location attribute: + provide the argument --mirroring-deployment-group on the command line with a fully specified name; + provide the argument --mirroring-deployment-group-location on the command line; + provide the argument networksecurity.projects.locations.mirroringDeployments on the command line with a fully specified name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Description of the mirroring deployment |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-wait` | MAX_WAIT | 20m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To create a mirroring deployment called my-deployment, in project ID
my-project and zone us-central1-a, run:        $ gcloud network-security mirroring-deployments create \
        my-deployment --project=my-project --location=us-central1-a \
        --deployment-group-location=global \
        --forwarding-rule=my-forwarding-rule \
        --forwarding-rule-location=us-central1 \
        --mirroring-deployment-group=my-deployment-group

OR

    $ gcloud network-security mirroring-deployments create \
        my-deployment --project=my-project --location=us-central1-a \
        --forwarding-rule=projects/my-project/regions/us-central1/\
    forwardingRules/my-forwarding-rule \
        --mirroring-deployment-group=projects/my-project/locations/\
    global/mirroringDeploymentGroups/my-deployment-group

OR

    $ gcloud network-security mirroring-deployments create \
        projects/my-project/locations/us-central1/mirroringDeployments/\
    my-deployment \
        --forwarding-rule=projects/my-project/regions/us-central1/\
    forwardingRules/my-forwarding-rule \
        --mirroring-deployment-group=projects/my-project/locations/\
    global/mirroringDeploymentGroups/my-deployment-group

OR

    $ gcloud network-security mirroring-deployments create \
        projects/my-project/locations/us-central1/mirroringDeployments/\
    my-deployment \
        --forwarding-rule=projects/my-project/regions/us-central1/\
    forwardingRules/my-forwarding-rule \
        --mirroring-deployment-group=projects/my-project/locations/\
    global/mirroringDeploymentGroups/my-deployment-group \
        --description="my-description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/mirroring-deployments/create)

---
### `gcloud network-security mirroring-deployments delete`

Delete a Mirroring Deployment

Delete a mirroring deployment. Check the progress of deployment deletion by
using gcloud network-security mirroring-deployments list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security mirroring-deployments delete
    (MIRRORING_DEPLOYMENT : --location=LOCATION) [--async]
    [--max-wait=MAX_WAIT; default="20m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Mirroring deployment resource - Mirroring Deployment. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument MIRRORING_DEPLOYMENT on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIRRORING_DEPLOYMENT
     ID of the mirroring deployment or fully qualified identifier for the
     mirroring deployment.

     To set the deployment-id attribute:
     + provide the argument MIRRORING_DEPLOYMENT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the mirroring deployment.

     To set the location attribute:
     + provide the argument MIRRORING_DEPLOYMENT on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--max-wait` | MAX_WAIT | 20m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To delete a mirroring deployment called my-deployment in location
us-central1, run:

    $ gcloud network-security mirroring-deployments delete \
        my-deployment --location=us-central1-a --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/mirroring-deployments/delete)

---
### `gcloud network-security mirroring-deployments describe`

Describe a Mirroring Deployment

Describe a mirroring deployment.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security mirroring-deployments describe
    (MIRRORING_DEPLOYMENT : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Mirroring deployment resource - Mirroring Deployment. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument MIRRORING_DEPLOYMENT on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIRRORING_DEPLOYMENT
     ID of the mirroring deployment or fully qualified identifier for the
     mirroring deployment.

     To set the deployment-id attribute:
     + provide the argument MIRRORING_DEPLOYMENT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the mirroring deployment.

     To set the location attribute:
     + provide the argument MIRRORING_DEPLOYMENT on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get a description of a mirroring deployment called my-deployment in zone
us-central1-a, run:

    $ gcloud network-security mirroring-deployments describe \
        my-deployment --location=us-central1-a --project=my-project

OR

    $ gcloud network-security mirroring-deployments describe \
        projects/my-project/locations/us-central1-a/\
    mirroringDeployments/my-deployment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/mirroring-deployments/describe)

---
### `gcloud network-security mirroring-deployments list`

List Mirroring Deployments

List mirroring deployments.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security mirroring-deployments list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + Location of the Mirroring Deployment. Defaults to a wildcard. |


**Examples:**
```bash
To list mirroring deployments in project my-project and zone us-central1-a,
run:

    $ gcloud network-security mirroring-deployments list \
        --project=my-project --location=us-central1-a

To list mirroring deployments from all zones, run:

    $ gcloud network-security mirroring-deployments list \
        --project=my-project --location=-
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/mirroring-deployments/list)

---
### `gcloud network-security mirroring-deployments update`

Update a Mirroring Deployment

Update a mirroring deployment. Check the progress of deployment update by
using gcloud network-security mirroring-deployments list.

For examples refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security mirroring-deployments update
    (MIRRORING_DEPLOYMENT : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--max-wait=MAX_WAIT; default="20m"]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Mirroring deployment resource - Mirroring Deployment. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument MIRRORING_DEPLOYMENT on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIRRORING_DEPLOYMENT
     ID of the mirroring deployment or fully qualified identifier for the
     mirroring deployment.

     To set the deployment-id attribute:
     + provide the argument MIRRORING_DEPLOYMENT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the mirroring deployment.

     To set the location attribute:
     + provide the argument MIRRORING_DEPLOYMENT on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Description of the mirroring deployment |
| `--max-wait` | MAX_WAIT | 20m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update labels k1 and k2, run:

    $ gcloud network-security mirroring-deployments update \
        my-deployment --project=my-project --location=us-central1-a \
        --update-labels=k1=v1,k2=v2

To remove labels k3 and k4, run:

    $ gcloud network-security mirroring-deployments update \
        my-deployment --project=my-project --location=us-central1-a \
        --remove-labels=k3,k4

To clear all labels from the mirroring deployment, run:

    $ gcloud network-security mirroring-deployments update \
        my-deploymen --project=my-project --location=us-central1-a \
        --clear-labels

To update description to 'new description', run:

    $ gcloud network-security mirroring-deployments update \
        my-deploymen --project=my-project --location=us-central1-a \
        --description="new description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/mirroring-deployments/update)

---