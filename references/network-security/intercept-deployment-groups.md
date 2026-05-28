# gcloud network-security intercept-deployment-groups

manage Intercept Deployment Group resources

### `gcloud network-security intercept-deployment-groups create`

Create an Intercept Deployment Group

Create an intercept deployment group. Successful creation of a deployment
group results in a deployment group in ACTIVE state. Check the progress of
deployment group creation by using gcloud network-security
intercept-deployment-groups list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-deployment-groups create
    (INTERCEPT_DEPLOYMENT_GROUP : --location=LOCATION) --network=NETWORK
    [--async] [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--max-wait=MAX_WAIT; default="20m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept deployment group resource - Intercept Deployment Group. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument INTERCEPT_DEPLOYMENT_GROUP on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_DEPLOYMENT_GROUP
     ID of the intercept deployment group or fully qualified identifier
     for the intercept deployment group.

     To set the deployment-group-id attribute:
     + provide the argument INTERCEPT_DEPLOYMENT_GROUP on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept deployment group.

     To set the location attribute:
     + provide the argument INTERCEPT_DEPLOYMENT_GROUP on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | _[This must be specified.]_ ID of the network or fully qualified identifier for the network. To set the network-name attribute: + provide the argument --network on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Description of the deployment group. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-wait` | MAX_WAIT | 20m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To create a intercept deployment group called my-deployment-group, in
project ID my-project, run:        $ gcloud network-security intercept-deployment-groups create \
        my-deployment-group --project=my-project --location=global \
        --network=my-network

OR

    $ gcloud network-security intercept-deployment-groups create \
        my-deployment-group --project=my-project --location=global \
        --network=projects/my-project/global/networks/my-network

OR

    $ gcloud network-security intercept-deployment-groups create \
        projects/my-project/locations/global/interceptDeploymentGroups/\
    my-deployment-group \
        --network=projects/my-project/global/networks/my-network

OR

    $ gcloud network-security intercept-deployment-groups create \
        projects/my-project/locations/global/interceptDeploymentGroups/\
    my-deployment-group \
        --network=projects/my-project/global/networks/my-network \
        --description='new description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-deployment-groups/create)

---
### `gcloud network-security intercept-deployment-groups delete`

Delete an Intercept Deployment Group

Delete an intercept deployment group. Check the progress of deployment
group deletion by using gcloud network-security intercept-deployment-groups
list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-deployment-groups delete
    (INTERCEPT_DEPLOYMENT_GROUP : --location=LOCATION) [--async]
    [--max-wait=MAX_WAIT; default="20m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept deployment group resource - Intercept Deployment Group. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument INTERCEPT_DEPLOYMENT_GROUP on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_DEPLOYMENT_GROUP
     ID of the intercept deployment group or fully qualified identifier
     for the intercept deployment group.

     To set the deployment-group-id attribute:
     + provide the argument INTERCEPT_DEPLOYMENT_GROUP on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept deployment group.

     To set the location attribute:
     + provide the argument INTERCEPT_DEPLOYMENT_GROUP on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--max-wait` | MAX_WAIT | 20m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To delete an intercept deployment group called my-deployment-group, in
project ID my-project, run:

    $ gcloud network-security intercept-deployment-groups delete \
        my-deployment-group --project=my-project --location=global

OR

    $ gcloud network-security intercept-deployment-groups delete \
        projects/my-project/locations/global/interceptDeploymentGroups/\
    my-deployment-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-deployment-groups/delete)

---
### `gcloud network-security intercept-deployment-groups describe`

Describe an Intercept Deployment Group

Describe an intercept deployment group.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-deployment-groups describe
    (INTERCEPT_DEPLOYMENT_GROUP : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept deployment group resource - Intercept Deployment Group. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument INTERCEPT_DEPLOYMENT_GROUP on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_DEPLOYMENT_GROUP
     ID of the intercept deployment group or fully qualified identifier
     for the intercept deployment group.

     To set the deployment-group-id attribute:
     + provide the argument INTERCEPT_DEPLOYMENT_GROUP on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept deployment group.

     To set the location attribute:
     + provide the argument INTERCEPT_DEPLOYMENT_GROUP on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get a description of an intercept deployment group called
my-deployment-group in project ID my-project, run:

    $ gcloud network-security intercept-deployment-groups describe \
        my-deployment-group --project=my-project --location=global

OR

    $ gcloud network-security intercept-deployment-groups describe \
        projects/my-project/locations/global/interceptDeploymentGroups/\
    my-deployment-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-deployment-groups/describe)

---
### `gcloud network-security intercept-deployment-groups list`

List Intercept Deployment Groups

List intercept deployment groups.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-deployment-groups list
    [--location=LOCATION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + Location of the Intercept Deployment Group. Defaults to global. |


**Examples:**
```bash
To list intercept deployment groups in project ID my-project, run:

    $ gcloud network-security intercept-deployment-groups list \
        --location=global --project=my-project

OR

    $ gcloud network-security intercept-deployment-groups list \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-deployment-groups/list)

---
### `gcloud network-security intercept-deployment-groups update`

Update an Intercept Deployment Group

Update an intercept deployment group. Check the progress of deployment
group update by using gcloud network-security intercept-deployment-groups
list.

For examples refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-deployment-groups update
    (INTERCEPT_DEPLOYMENT_GROUP : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--max-wait=MAX_WAIT; default="20m"]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept deployment group resource - Intercept Deployment Group. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument INTERCEPT_DEPLOYMENT_GROUP on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_DEPLOYMENT_GROUP
     ID of the intercept deployment group or fully qualified identifier
     for the intercept deployment group.

     To set the deployment-group-id attribute:
     + provide the argument INTERCEPT_DEPLOYMENT_GROUP on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept deployment group.

     To set the location attribute:
     + provide the argument INTERCEPT_DEPLOYMENT_GROUP on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Description of the deployment group. |
| `--max-wait` | MAX_WAIT | 20m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update labels k1 and k2, run:

    $ gcloud network-security intercept-deployment-groups update \
        my-deployment-group --project=my-project --location=global \
        --update-labels=k1=v1,k2=v2

To remove labels k3 and k4, run:

    $ gcloud network-security intercept-deployment-groups update \
        my-deployment-group --project=my-project --location=global \
        --remove-labels=k3,k4

To clear all labels from the intercept deployment group, run:

    $ gcloud network-security intercept-deployment-groups update \
        my-deployment-group --project=my-project --location=global \
        --clear-labels

To update description to 'new description', run:

    $ gcloud network-security intercept-deployment-groups update \
        my-deployment-group --project=my-project --location=global \
        --description='new description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-deployment-groups/update)

---