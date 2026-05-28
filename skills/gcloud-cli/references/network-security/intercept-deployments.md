# gcloud network-security intercept-deployments

manage Intercept Deployment resources

### `gcloud network-security intercept-deployments create`

Create an Intercept Deployment

Create an intercept deployment. Successful creation of a deployment results
in a deployment in ACTIVE state. Check the progress of deployment creation
by using gcloud network-security intercept-deployments list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-deployments create
    (INTERCEPT_DEPLOYMENT : --location=LOCATION)
    (--forwarding-rule=FORWARDING_RULE
      : --forwarding-rule-location=FORWARDING_RULE_LOCATION)
    (--intercept-deployment-group=INTERCEPT_DEPLOYMENT_GROUP
      : --intercept-deployment-group-location=INTERCEPT_DEPLOYMENT_GROUP_LOCATION)
    [--async] [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--max-wait=MAX_WAIT; default="20m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept deployment resource - Intercept Deployment. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument INTERCEPT_DEPLOYMENT on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_DEPLOYMENT
     ID of the intercept deployment or fully qualified identifier for the
     intercept deployment.

     To set the deployment-id attribute:
     + provide the argument INTERCEPT_DEPLOYMENT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept deployment.

     To set the location attribute:
     + provide the argument INTERCEPT_DEPLOYMENT on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--forwarding-rule` | FORWARDING_RULE |  | _[This must be specified.]_ ID of the forwardingRule or fully qualified identifier for the forwardingRule. To set the forwarding-rule-id attribute: + provide the argument --forwarding-rule on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--forwarding-rule-location` | FORWARDING_RULE_LOCATION |  | _[This must be specified.]_ The Cloud region for the forwardingRule. To set the forwarding-rule-location attribute: + provide the argument --forwarding-rule on the command line with a fully specified name; + provide the argument --forwarding-rule-location on the command line. |
| `--intercept-deployment-group` | INTERCEPT_DEPLOYMENT_GROUP |  | _[This must be specified.]_ ID of the intercept deployment group or fully qualified identifier for the intercept deployment group. To set the id attribute: + provide the argument --intercept-deployment-group on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--intercept-deployment-group-location` | INTERCEPT_DEPLOYMENT_GROUP_LOCATION |  | _[This must be specified.]_ Location of the intercept deployment group. To set the location attribute: + provide the argument --intercept-deployment-group on the command line with a fully specified name; + provide the argument --intercept-deployment-group-location on the command line; + provide the argument networksecurity.projects.locations.interceptDeployments on the command line with a fully specified name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Description of the deployment. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-wait` | MAX_WAIT | 20m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To create an intercept deployment called my-deployment, in project ID
my-project and zone us-central1-a, run:        $ gcloud network-security intercept-deployments create \
        my-deployment --project=my-project --location=us-central1-a \
        --deployment-group-location=global \
        --forwarding-rule=my-forwarding-rule \
        --forwarding-rule-location=us-central1 \
        --intercept-deployment-group=my-deployment-group

OR

    $ gcloud network-security intercept-deployments create \
        my-deployment --project=my-project --location=us-central1-a \
        --forwarding-rule=projects/my-project/regions/us-central1/\
    forwardingRules/my-forwarding-rule \
        --intercept-deployment-group=projects/my-project/locations/\
    global/interceptDeploymentGroups/my-deployment-group

OR

    $ gcloud network-security intercept-deployments create \
        projects/my-project/locations/us-central1/interceptDeployments/\
    my-deployment \
        --forwarding-rule=projects/my-project/regions/us-central1/\
    forwardingRules/my-forwarding-rule \
        --intercept-deployment-group=projects/my-project/locations/\
    global/interceptDeploymentGroups/my-deployment-group

OR

    $ gcloud network-security intercept-deployments create \
        projects/my-project/locations/us-central1/interceptDeployments/\
    my-deployment \
        --forwarding-rule=projects/my-project/regions/us-central1/\
    forwardingRules/my-forwarding-rule \
        --intercept-deployment-group=projects/my-project/locations/\
    global/interceptDeploymentGroups/my-deployment-group \
        --description="my-description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-deployments/create)

---
### `gcloud network-security intercept-deployments delete`

Delete an Intercept Deployment

Delete an intercept deployment. Check the progress of deployment deletion
by using gcloud network-security intercept-deployments list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-deployments delete
    (INTERCEPT_DEPLOYMENT : --location=LOCATION) [--async]
    [--max-wait=MAX_WAIT; default="20m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept deployment resource - Intercept Deployment. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument INTERCEPT_DEPLOYMENT on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_DEPLOYMENT
     ID of the intercept deployment or fully qualified identifier for the
     intercept deployment.

     To set the deployment-id attribute:
     + provide the argument INTERCEPT_DEPLOYMENT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept deployment.

     To set the location attribute:
     + provide the argument INTERCEPT_DEPLOYMENT on the command line
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
To delete an intercept deployment called my-deployment in location
us-central1, run:

    $ gcloud network-security intercept-deployments delete \
        my-deployment --location=us-central1-a --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-deployments/delete)

---
### `gcloud network-security intercept-deployments describe`

Describe an Intercept Deployment

Describe an intercept deployment.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-deployments describe
    (INTERCEPT_DEPLOYMENT : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept deployment resource - Intercept Deployment. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument INTERCEPT_DEPLOYMENT on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_DEPLOYMENT
     ID of the intercept deployment or fully qualified identifier for the
     intercept deployment.

     To set the deployment-id attribute:
     + provide the argument INTERCEPT_DEPLOYMENT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept deployment.

     To set the location attribute:
     + provide the argument INTERCEPT_DEPLOYMENT on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get a description of an intercept deployment called my-deployment in
zone us-central1-a, run:

    $ gcloud network-security intercept-deployments describe \
        my-deployment --location=us-central1-a --project=my-project

OR

    $ gcloud network-security intercept-deployments describe \
        projects/my-project/locations/us-central1-a/\
    interceptDeployments/my-deployment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-deployments/describe)

---
### `gcloud network-security intercept-deployments list`

List Intercept Deployments

List intercept deployments.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-deployments list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + Location of the Intercept Deployment. Defaults to a wildcard. |


**Examples:**
```bash
To list intercept deployments in project my-project and zone us-central1-a,
run:

    $ gcloud network-security intercept-deployments list \
        --project=my-project --location=us-central1-a

To list intercept deployments from all zones, run:

    $ gcloud network-security intercept-deployments list \
        --project=my-project --location=-
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-deployments/list)

---
### `gcloud network-security intercept-deployments update`

Update an Intercept Deployment

Update an intercept deployment. Check the progress of deployment update by
using gcloud network-security intercept-deployments list.

For examples refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-deployments update
    (INTERCEPT_DEPLOYMENT : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--max-wait=MAX_WAIT; default="20m"]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept deployment resource - Intercept Deployment. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument INTERCEPT_DEPLOYMENT on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_DEPLOYMENT
     ID of the intercept deployment or fully qualified identifier for the
     intercept deployment.

     To set the deployment-id attribute:
     + provide the argument INTERCEPT_DEPLOYMENT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept deployment.

     To set the location attribute:
     + provide the argument INTERCEPT_DEPLOYMENT on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Description of the deployment. |
| `--max-wait` | MAX_WAIT | 20m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update labels k1 and k2, run:

    $ gcloud network-security intercept-deployments update \
        my-deployment --project=my-project --location=us-central1-a \
        --update-labels=k1=v1,k2=v2

To remove labels k3 and k4, run:

    $ gcloud network-security intercept-deployments update \
        my-deployment --project=my-project --location=us-central1-a \
        --remove-labels=k3,k4

To clear all labels from the intercept deployment, run:

    $ gcloud network-security intercept-deployments update \
        my-deploymen --project=my-project --location=us-central1-a \
        --clear-labels

To update description to 'new description', run:

    $ gcloud network-security intercept-deployments update \
        my-deploymen --project=my-project --location=us-central1-a \
        --description="new description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-deployments/update)

---