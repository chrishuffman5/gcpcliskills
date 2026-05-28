# gcloud network-security intercept-endpoint-groups

manage Intercept Endpoint Group resources

### `gcloud network-security intercept-endpoint-groups create`

Create a Intercept Endpoint Group

Create a intercept endpoint group. Successful creation of an endpoint group
results in an endpoint group in ACTIVE state. Check the progress of
endpoint group creation by using gcloud network-security
intercept-endpoint-groups list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-endpoint-groups create
    (INTERCEPT_ENDPOINT_GROUP : --location=LOCATION)
    (--intercept-deployment-group=INTERCEPT_DEPLOYMENT_GROUP
      : --intercept-deployment-group-location=INTERCEPT_DEPLOYMENT_GROUP_LOCATION --intercept-deployment-group-project=INTERCEPT_DEPLOYMENT_GROUP_PROJECT)
    [--async] [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--max-wait=MAX_WAIT; default="20m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept endpoint group resource - Intercept Endpoint Group. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument INTERCEPT_ENDPOINT_GROUP on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_ENDPOINT_GROUP
     ID of the intercept endpoint group or fully qualified identifier for
     the intercept endpoint group.

     To set the endpoint-group-id attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept endpoint group.

     To set the location attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--intercept-deployment-group` | INTERCEPT_DEPLOYMENT_GROUP |  | _[This must be specified.]_ ID of the intercept deployment group or fully qualified identifier for the intercept deployment group. To set the id attribute: + provide the argument --intercept-deployment-group on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--intercept-deployment-group-location` | INTERCEPT_DEPLOYMENT_GROUP_LOCATION |  | _[This must be specified.]_ Location of the intercept deployment group. To set the location attribute: + provide the argument --intercept-deployment-group on the command line with a fully specified name; + provide the argument --intercept-deployment-group-location on the command line; + provide the argument --location on the command line; + provide the argument INTERCEPT_ENDPOINT_GROUP on the command line with a fully specified name. |
| `--intercept-deployment-group-project` | INTERCEPT_DEPLOYMENT_GROUP_PROJECT |  | _[This must be specified.]_ Project of the intercept deployment group. To set the project attribute: + provide the argument --intercept-deployment-group on the command line with a fully specified name; + provide the argument --intercept-deployment-group-project on the command line; + provide the argument --project on the command line; + set the property core/project; + provide the argument INTERCEPT_ENDPOINT_GROUP on the command line with a fully specified name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Description of the endpoint |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-wait` | MAX_WAIT | 20m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To create a intercept endpoint group called my-endpoint-group, in project
ID my-project, run:        $ gcloud network-security intercept-endpoint-groups create \
        my-endpoint-group --project=my-project --location=global \
        --intercept-deployment-group=my-deployment-group

OR

    $ gcloud network-security intercept-endpoint-groups create \
        my-endpoint-group --project=my-project --location=global \
        --intercept-deployment-group=projects/my-project/locations/\
    global/interceptDeploymentGroups/my-deployment-group

OR

    $ gcloud network-security intercept-endpoint-groups create \
        projects/my-project/locations/global/interceptEndpointGroups/\
    my-endpoint-group \
        --intercept-deployment-group=projects/my-project/locations/\
    global/interceptDeploymentGroups/my-deployment-group

OR

    $ gcloud network-security intercept-endpoint-groups create \
        my-endpoint-group --project=my-project --location=global \
        --mirroring-deployment-group=projects/my-project/locations/\
    global/interceptDeploymentGroups/my-deployment-group \
        --description='new description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-endpoint-groups/create)

---
### `gcloud network-security intercept-endpoint-groups delete`

Delete a Intercept Endpoint Group

Delete a intercept endpoint group. Check the progress of endpoint group
deletion by using gcloud network-security intercept-endpoint-groups list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-endpoint-groups delete
    (INTERCEPT_ENDPOINT_GROUP : --location=LOCATION) [--async]
    [--max-wait=MAX_WAIT; default="20m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept endpoint group resource - Intercept Endpoint Group. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument INTERCEPT_ENDPOINT_GROUP on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_ENDPOINT_GROUP
     ID of the intercept endpoint group or fully qualified identifier for
     the intercept endpoint group.

     To set the endpoint-group-id attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept endpoint group.

     To set the location attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP on the command line
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
To delete a intercept endpoint group called my-endpoint-group, in project
ID my-project, run:        $ gcloud network-security intercept-endpoint-groups delete \
        my-endpoint-group --project=my-project --location=global

OR

    $ gcloud network-security intercept-endpoint-groups delete \
        projects/my-project/locations/global/interceptEndpointGroups/\
    my-endpoint-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-endpoint-groups/delete)

---
### `gcloud network-security intercept-endpoint-groups describe`

Describe a Intercept Endpoint Group

Describe a intercept endpoint group.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-endpoint-groups describe
    (INTERCEPT_ENDPOINT_GROUP : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept endpoint group resource - Intercept Endpoint Group. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument INTERCEPT_ENDPOINT_GROUP on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_ENDPOINT_GROUP
     ID of the intercept endpoint group or fully qualified identifier for
     the intercept endpoint group.

     To set the endpoint-group-id attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept endpoint group.

     To set the location attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get a description of a intercept endpoint group called my-endpoint-group
in project ID my-project, run:        $ gcloud network-security intercept-endpoint-groups describe \
        my-endpoint-group --project=my-project --location=global

OR

    $ gcloud network-security intercept-endpoint-groups describe \
        projects/my-project/locations/global/interceptEndpointGroups/\
    my-endpoint-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-endpoint-groups/describe)

---
### `gcloud network-security intercept-endpoint-groups list`

List Intercept Endpoint Groups

List intercept endpoint groups.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-endpoint-groups list
    [--location=LOCATION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + Location of the Intercept Endpoint Group. Defaults to global. |


**Examples:**
```bash
To list intercept endpoint groups in project ID my-project, run:        $ gcloud network-security intercept-endpoint-groups list \
        --project=my-project --location=global

OR

    $ gcloud network-security intercept-endpoint-groups list \
        --location=global

OR

    $ gcloud network-security intercept-endpoint-groups list \
        --location=projects/my-project/locations/global

OR

    $ gcloud network-security intercept-endpoint-groups list \
        projects/my-project/locations/global/interceptEndpointGroups
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-endpoint-groups/list)

---
### `gcloud network-security intercept-endpoint-groups update`

Update a Intercept Endpoint Group

Update a intercept endpoint groups. Check the progress of endpoint group
update by using gcloud network-security intercept-endpoint-groups list.

For examples refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-endpoint-groups update
    (INTERCEPT_ENDPOINT_GROUP : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--max-wait=MAX_WAIT; default="20m"]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept endpoint group resource - Intercept Endpoint Group. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument INTERCEPT_ENDPOINT_GROUP on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_ENDPOINT_GROUP
     ID of the intercept endpoint group or fully qualified identifier for
     the intercept endpoint group.

     To set the endpoint-group-id attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept endpoint group.

     To set the location attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP on the command line
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

    $ gcloud network-security intercept-endpoint-groups update \
        my-endpoint-group --project=my-project \
        --location=us-central1-a --update-labels=k1=v1,k2=v2

To remove labels k3 and k4, run:

    $ gcloud network-security intercept-endpoint-groups update \
        my-endpoint-group --project=my-project \
        --location=us-central1-a --remove-labels=k3,k4

To clear all labels from the intercept endpoint group, run:

    $ gcloud network-security intercept-endpoint-groups update \
        my-endpoint-group --project=my-project \
        --location=us-central1-a --clear-labels

To update description to 'new description', run:

    $ gcloud network-security intercept-endpoint-groups update \
        my-endpoint-group --project=my-project \
        --location=us-central1-a --description='new description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-endpoint-groups/update)

---