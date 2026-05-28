# gcloud network-security intercept-endpoint-group-associations

manage Intercept Endpoint Group Association resources

### `gcloud network-security intercept-endpoint-group-associations create`

Create an Intercept Endpoint Group Association

Create an intercept endpoint group association. Successful creation of an
association results in an association in ACTIVE state. Check the progress
of association creation by using gcloud network-security
intercept-endpoint-group-associations list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-endpoint-group-associations create
    (INTERCEPT_ENDPOINT_GROUP_ASSOCIATION : --location=LOCATION)
    --network=NETWORK
    (--intercept-endpoint-group=INTERCEPT_ENDPOINT_GROUP
      : --intercept-endpoint-group-location=INTERCEPT_ENDPOINT_GROUP_LOCATION)
    [--async] [--labels=[KEY=VALUE,...]]
    [--max-wait=MAX_WAIT; default="20m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept endpoint group association resource - Intercept Endpoint Group
Association. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument INTERCEPT_ENDPOINT_GROUP_ASSOCIATION on the
   command line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_ENDPOINT_GROUP_ASSOCIATION
     ID of the intercept endpoint group association or fully qualified
     identifier for the intercept endpoint group association.

     To set the endpoint-group-association-id attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP_ASSOCIATION on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept endpoint group association.

     To set the location attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP_ASSOCIATION on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | _[This must be specified.]_ ID of the network or fully qualified identifier for the network. To set the network-name attribute: + provide the argument --network on the command line. |
| `--intercept-endpoint-group` | INTERCEPT_ENDPOINT_GROUP |  | _[This must be specified.]_ ID of the intercept endpoint group or fully qualified identifier for the intercept endpoint group. To set the id attribute: + provide the argument --intercept-endpoint-group on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--intercept-endpoint-group-location` | INTERCEPT_ENDPOINT_GROUP_LOCATION |  | _[This must be specified.]_ Location of the intercept endpoint group. To set the location attribute: + provide the argument --intercept-endpoint-group on the command line with a fully specified name; + provide the argument --intercept-endpoint-group-location on the command line; + provide the argument --location on the command line; + provide the argument networksecurity.projects.locations.interceptEndpointGroupAssociations on the command line with a fully specified name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-wait` | MAX_WAIT | 20m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To create an intercept endpoint group association called my-association, in
project ID my-project, run:

$ gcloud network-security intercept-endpoint-group-associations \        create my-association --project=my-project --location=global \
    --intercept-endpoint-group=my-endpoint-group \
    --network=my-network

OR

$ gcloud network-security intercept-endpoint-group-associations \        create my-association --project=my-project --location=global \
    --intercept-endpoint-group=my-endpoint-group \
    --network=projects/my-project/global/networks/my-network

OR

$ gcloud network-security intercept-endpoint-group-associations \        create \
    projects/my-project/locations/global/\
    interceptEndpointGroupAssociations/my-association \
        --intercept-endpoint-group=projects/my-project/locations/\
    global/interceptEndpointGroups/my-endpoint-group \
        --network=projects/my-project/global/networks/my-network
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-endpoint-group-associations/create)

---
### `gcloud network-security intercept-endpoint-group-associations delete`

Delete an Intercept Endpoint Group Association

Delete an intercept endpoint group association. Check the progress of
deletion by using gcloud network-security
intercept-endpoint-group-associations list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-endpoint-group-associations delete
    (INTERCEPT_ENDPOINT_GROUP_ASSOCIATION : --location=LOCATION) [--async]
    [--max-wait=MAX_WAIT; default="20m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept endpoint group association resource - Intercept Endpoint Group
Association. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument INTERCEPT_ENDPOINT_GROUP_ASSOCIATION on the
   command line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_ENDPOINT_GROUP_ASSOCIATION
     ID of the intercept endpoint group association or fully qualified
     identifier for the intercept endpoint group association.

     To set the endpoint-group-association-id attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP_ASSOCIATION on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept endpoint group association.

     To set the location attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP_ASSOCIATION on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--max-wait` | MAX_WAIT | 20m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To delete an intercept endpoint group association called my-association, in
project ID my-project, run:

$ gcloud network-security intercept-endpoint-group-associations \        delete my-association --project=my-project --location=global

OR

$ gcloud network-security intercept-endpoint-group-associations \        delete \
    projects/my-project/locations/global/\
    interceptEndpointGroupAssociations/my-association
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-endpoint-group-associations/delete)

---
### `gcloud network-security intercept-endpoint-group-associations describe`

Describe an Intercept Endpoint Group Association

Describe an intercept endpoint group association.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-endpoint-group-associations describe
    (INTERCEPT_ENDPOINT_GROUP_ASSOCIATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept endpoint group association resource - Intercept Endpoint Group
Association. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument INTERCEPT_ENDPOINT_GROUP_ASSOCIATION on the
   command line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_ENDPOINT_GROUP_ASSOCIATION
     ID of the intercept endpoint group association or fully qualified
     identifier for the intercept endpoint group association.

     To set the endpoint-group-association-id attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP_ASSOCIATION on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept endpoint group association.

     To set the location attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP_ASSOCIATION on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get a description of an intercept endpoint group association called
my-association in project my-project and location global, run:

$ gcloud network-security intercept-endpoint-group-associations \        describe my-association --project=my-project --location=global

OR

$ gcloud network-security intercept-endpoint-group-associations \        describe \
    projects/my-project/locations/global/\
    interceptEndpointGroupAssociations/my-association
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-endpoint-group-associations/describe)

---
### `gcloud network-security intercept-endpoint-group-associations list`

List Intercept Endpoint Group Associations

List intercept endpoint group associations.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-endpoint-group-associations list
    [--location=LOCATION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + Location of the Intercept Endpoint Group Association. Defaults to global. |


**Examples:**
```bash
To list intercept endpoint group associations in project my-project and
location global, run:

$ gcloud network-security intercept-endpoint-group-associations \        list --project=my-project --location=global

OR

$ gcloud network-security intercept-endpoint-group-associations \        list --location=global

OR

$ gcloud network-security intercept-endpoint-group-associations \        list --location=projects/my-project/locations/global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-endpoint-group-associations/list)

---
### `gcloud network-security intercept-endpoint-group-associations update`

Update an Intercept Endpoint Group Association

Update an intercept endpoint group association. Check the progress of
association update by using gcloud network-security
intercept-endpoint-group-associations list.

For examples refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security intercept-endpoint-group-associations update
    (INTERCEPT_ENDPOINT_GROUP_ASSOCIATION : --location=LOCATION) [--async]
    [--max-wait=MAX_WAIT; default="20m"] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Intercept endpoint group association resource - Intercept Endpoint Group
Association. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument INTERCEPT_ENDPOINT_GROUP_ASSOCIATION on the
   command line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCEPT_ENDPOINT_GROUP_ASSOCIATION
     ID of the intercept endpoint group association or fully qualified
     identifier for the intercept endpoint group association.

     To set the endpoint-group-association-id attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP_ASSOCIATION on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the intercept endpoint group association.

     To set the location attribute:
     + provide the argument INTERCEPT_ENDPOINT_GROUP_ASSOCIATION on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--max-wait` | MAX_WAIT | 20m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update labels k1 and k2, run:

$ gcloud network-security intercept-endpoint-group-associations \        update my-association --project=my-project --location=global \
    --update-labels=k1=v1,k2=v2

To remove labels k3 and k4, run:

$ gcloud network-security intercept-endpoint-group-associations \        update my-association --project=my-project --location=global \
    --remove-labels=k3,k4

To clear all labels from the intercept endpoint group association, run:

$ gcloud network-security intercept-endpoint-group-associations \        update my-association --project=my-project --location=global \
    --clear-labels
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/intercept-endpoint-group-associations/update)

---