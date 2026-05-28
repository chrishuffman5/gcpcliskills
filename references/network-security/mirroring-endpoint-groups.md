# gcloud network-security mirroring-endpoint-groups

manage Mirroring Endpoint Group resources

### `gcloud network-security mirroring-endpoint-groups create`

Create a Mirroring Endpoint Group

Create a mirroring endpoint group. Successful creation of an endpoint group
results in an endpoint group in ACTIVE state. Check the progress of
endpoint group creation by using gcloud network-security
mirroring-endpoint-groups list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security mirroring-endpoint-groups create
    (MIRRORING_ENDPOINT_GROUP : --location=LOCATION)
    ([--mirroring-deployment-group=MIRRORING_DEPLOYMENT_GROUP
      : --mirroring-deployment-group-location=MIRRORING_DEPLOYMENT_GROUP_LOCATION --mirroring-deployment-group-project=MIRRORING_DEPLOYMENT_GROUP_PROJECT])
    [--async] [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--max-wait=MAX_WAIT; default="20m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Mirroring endpoint group resource - Mirroring Endpoint Group. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument MIRRORING_ENDPOINT_GROUP on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIRRORING_ENDPOINT_GROUP
     ID of the mirroring endpoint group or fully qualified identifier for
     the mirroring endpoint group.

     To set the endpoint-group-id attribute:
     + provide the argument MIRRORING_ENDPOINT_GROUP on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the mirroring endpoint group.

     To set the location attribute:
     + provide the argument MIRRORING_ENDPOINT_GROUP on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--mirroring-deployment-group` | MIRRORING_DEPLOYMENT_GROUP |  | _[resource.]_ ID of the mirroring deployment group or fully qualified identifier for the mirroring deployment group. To set the id attribute: - provide the argument --mirroring-deployment-group on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--mirroring-deployment-group-location` | MIRRORING_DEPLOYMENT_GROUP_LOCATION |  | _[resource.]_ Location of the mirroring deployment group. To set the location attribute: - provide the argument --mirroring-deployment-group on the command line with a fully specified name; - provide the argument --mirroring-deployment-group-location on the command line; - provide the argument --location on the command line; - provide the argument MIRRORING_ENDPOINT_GROUP on the command line with a fully specified name. |
| `--mirroring-deployment-group-project` | MIRRORING_DEPLOYMENT_GROUP_PROJECT |  | _[resource.]_ Project of the mirroring deployment group. To set the project attribute: - provide the argument --mirroring-deployment-group on the command line with a fully specified name; - provide the argument --mirroring-deployment-group-project on the command line; - provide the argument --project on the command line; - set the property core/project; - provide the argument MIRRORING_ENDPOINT_GROUP on the command line with a fully specified name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Description of the endpoint |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-wait` | MAX_WAIT | 20m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To create a mirroring endpoint group called my-endpoint-group, in project
ID my-project, run:        $ gcloud network-security mirroring-endpoint-groups create \
        my-endpoint-group --project=my-project --location=global \
        --mirroring-deployment-group=my-deployment-group

OR

    $ gcloud network-security mirroring-endpoint-groups create \
        my-endpoint-group --project=my-project --location=global \
        --mirroring-deployment-group=projects/my-project/locations/\
    global/mirroringDeploymentGroups/my-deployment-group

OR

    $ gcloud network-security mirroring-endpoint-groups create \
        projects/my-project/locations/global/mirroringEndpointGroups/\
    my-endpoint-group \
        --mirroring-deployment-group=projects/my-project/locations/\
    global/mirroringDeploymentGroups/my-deployment-group

OR

    $ gcloud network-security mirroring-endpoint-groups create \
        my-endpoint-group --project=my-project --location=global \
        --mirroring-deployment-group=projects/my-project/locations/\
    global/mirroringDeploymentGroups/my-deployment-group \
        --description='new description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/mirroring-endpoint-groups/create)

---
### `gcloud network-security mirroring-endpoint-groups delete`

Delete a Mirroring Endpoint Group

Delete a mirroring endpoint group. Check the progress of endpoint group
deletion by using gcloud network-security mirroring-endpoint-groups list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security mirroring-endpoint-groups delete
    (MIRRORING_ENDPOINT_GROUP : --location=LOCATION) [--async]
    [--max-wait=MAX_WAIT; default="20m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Mirroring endpoint group resource - Mirroring Endpoint Group. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument MIRRORING_ENDPOINT_GROUP on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIRRORING_ENDPOINT_GROUP
     ID of the mirroring endpoint group or fully qualified identifier for
     the mirroring endpoint group.

     To set the endpoint-group-id attribute:
     + provide the argument MIRRORING_ENDPOINT_GROUP on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the mirroring endpoint group.

     To set the location attribute:
     + provide the argument MIRRORING_ENDPOINT_GROUP on the command line
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
To delete a mirroring endpoint group called my-endpoint-group, in project
ID my-project, run:        $ gcloud network-security mirroring-endpoint-groups delete \
        my-endpoint-group --project=my-project --location=global

OR

    $ gcloud network-security mirroring-endpoint-groups delete \
        projects/my-project/locations/global/mirroringEndpointGroups/\
    my-endpoint-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/mirroring-endpoint-groups/delete)

---
### `gcloud network-security mirroring-endpoint-groups describe`

Describe a Mirroring Endpoint Group

Describe a mirroring endpoint group.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security mirroring-endpoint-groups describe
    (MIRRORING_ENDPOINT_GROUP : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Mirroring endpoint group resource - Mirroring Endpoint Group. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument MIRRORING_ENDPOINT_GROUP on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIRRORING_ENDPOINT_GROUP
     ID of the mirroring endpoint group or fully qualified identifier for
     the mirroring endpoint group.

     To set the endpoint-group-id attribute:
     + provide the argument MIRRORING_ENDPOINT_GROUP on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the mirroring endpoint group.

     To set the location attribute:
     + provide the argument MIRRORING_ENDPOINT_GROUP on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get a description of a mirroring endpoint group called my-endpoint-group
in project ID my-project, run:        $ gcloud network-security mirroring-endpoint-groups describe \
        my-endpoint-group --project=my-project --location=global

OR

    $ gcloud network-security mirroring-endpoint-groups describe \
        projects/my-project/locations/global/mirroringEndpointGroups/\
    my-endpoint-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/mirroring-endpoint-groups/describe)

---
### `gcloud network-security mirroring-endpoint-groups list`

List Mirroring Endpoint Groups

List mirroring endpoint groups.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security mirroring-endpoint-groups list
    [--location=LOCATION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + Location of the Mirroring Endpoint Group. Defaults to global. |


**Examples:**
```bash
To list mirroring endpoint groups in project ID my-project, run:        $ gcloud network-security mirroring-endpoint-groups list \
        --project=my-project --location=global

OR

    $ gcloud network-security mirroring-endpoint-groups list \
        --location=global

OR

    $ gcloud network-security mirroring-endpoint-groups list \
        --location=projects/my-project/locations/global

OR

    $ gcloud network-security mirroring-endpoint-groups list \
        projects/my-project/locations/global/mirroringEndpointGroups
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/mirroring-endpoint-groups/list)

---
### `gcloud network-security mirroring-endpoint-groups update`

Update a Mirroring Endpoint Group

Update a mirroring endpoint groups. Check the progress of endpoint group
update by using gcloud network-security mirroring-endpoint-groups list.

For examples refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security mirroring-endpoint-groups update
    (MIRRORING_ENDPOINT_GROUP : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--max-wait=MAX_WAIT; default="20m"]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Mirroring endpoint group resource - Mirroring Endpoint Group. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument MIRRORING_ENDPOINT_GROUP on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIRRORING_ENDPOINT_GROUP
     ID of the mirroring endpoint group or fully qualified identifier for
     the mirroring endpoint group.

     To set the endpoint-group-id attribute:
     + provide the argument MIRRORING_ENDPOINT_GROUP on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the mirroring endpoint group.

     To set the location attribute:
     + provide the argument MIRRORING_ENDPOINT_GROUP on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Description of the endpoint |
| `--max-wait` | MAX_WAIT | 20m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update labels k1 and k2, run:

    $ gcloud network-security mirroring-endpoint-groups update \
        my-endpoint-group --project=my-project \
        --location=us-central1-a --update-labels=k1=v1,k2=v2

To remove labels k3 and k4, run:

    $ gcloud network-security mirroring-endpoint-groups update \
        my-endpoint-group --project=my-project \
        --location=us-central1-a --remove-labels=k3,k4

To clear all labels from the mirroring endpoint group, run:

    $ gcloud network-security mirroring-endpoint-groups update \
        my-endpoint-group --project=my-project \
        --location=us-central1-a --clear-labels

To update description to 'new description', run:

    $ gcloud network-security mirroring-endpoint-groups update \
        my-endpoint-group --project=my-project \
        --location=us-central1-a --description='new description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/mirroring-endpoint-groups/update)

---