# gcloud netapp host-groups

create and manage Cloud NetApp Host Groups

### `gcloud netapp host-groups create`

Create a Cloud NetApp Host Group

Create a Cloud NetApp Host Group.

**Synopsis:**
```
gcloud netapp host-groups create (HOST_GROUP : --location=LOCATION)
    --hosts=HOST,[HOST,...] --os-type=OS_TYPE --type=TYPE [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Host group resource - The Host Group to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument host_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HOST_GROUP
     ID of the host_group or fully qualified identifier for the
     host_group.

     To set the host_group attribute:
     + provide the argument host_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the host_group.

     To set the location attribute:
     + provide the argument host_group on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hosts` | HOST,[HOST,...] |  | List of hosts in the host group. |
| `--os-type` | one of: LINUX, WINDOWS, ESXI |  | String indicating the OS type of the hosts in the host group. The supported values are: 'LINUX', 'WINDOWS', 'ESXI'. OS_TYPE must be one of: LINUX, WINDOWS, ESXI. |
| `--type` | TYPE |  | String indicating the type of host group. The supported values are: 'ISCSI_INITIATOR'. TYPE must be (only one value is supported): ISCSI_INITIATOR. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Host Group |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command creates a Host Group named NAME using the required
arguments:

    $ gcloud netapp host-groups create NAME --location=us-central1 \
      --type=ISCSI_INITIATOR --hosts=host1,host2 --os-type=LINUX
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/host-groups/create)

---
### `gcloud netapp host-groups delete`

Delete a Cloud NetApp Host Group

Delete a Cloud NetApp Host Group.

**Synopsis:**
```
gcloud netapp host-groups delete (HOST_GROUP : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Host group resource - The Host Group to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument host_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HOST_GROUP
     ID of the host_group or fully qualified identifier for the
     host_group.

     To set the host_group attribute:
     + provide the argument host_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the host_group.

     To set the location attribute:
     + provide the argument host_group on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes a Host Group named NAME:

    $ gcloud netapp host-groups delete NAME --location=us-central1

To delete a Host Group named NAME asynchronously, run the following
command:

    $ gcloud netapp host-groups delete NAME --location=us-central1 \
      --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/host-groups/delete)

---
### `gcloud netapp host-groups describe`

Describe a Cloud NetApp Host Group

Describe a Cloud NetApp Host Group.

**Synopsis:**
```
gcloud netapp host-groups describe (HOST_GROUP : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Host group resource - The Host Group to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument host_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HOST_GROUP
     ID of the host_group or fully qualified identifier for the
     host_group.

     To set the host_group attribute:
     + provide the argument host_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the host_group.

     To set the location attribute:
     + provide the argument host_group on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Examples:**
```bash
The following command describes a Host Group named NAME in the given
location:

    $ gcloud netapp host-groups describe NAME --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/host-groups/describe)

---
### `gcloud netapp host-groups list`

List Cloud NetApp Host Groups

Lists Cloud NetApp Host Groups.

**Synopsis:**
```
gcloud netapp host-groups list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + uses all locations by default.; + set the property netapp/location. |


**Examples:**
```bash
The following command lists all Host Groups in the given location:

    $ gcloud netapp host-groups list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/host-groups/list)

---
### `gcloud netapp host-groups update`

Update a Cloud NetApp Host Group

Update a Cloud NetApp Host Group and its specified parameters.

**Synopsis:**
```
gcloud netapp host-groups update (HOST_GROUP : --location=LOCATION)
    [--async] [--description=DESCRIPTION] [--hosts=HOST,[HOST,...]]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Host group resource - The Host Group to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument host_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HOST_GROUP
     ID of the host_group or fully qualified identifier for the
     host_group.

     To set the host_group attribute:
     + provide the argument host_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the host_group.

     To set the location attribute:
     + provide the argument host_group on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Host Group |
| `--hosts` | HOST,[HOST,...] |  | List of hosts in the host group. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command updates a Host Group named NAME and its specified
parameters:

    $ gcloud netapp host-groups update NAME --location=us-central1 \
      --description="new description" --hosts="host3,host4" \
      --update-labels=key2=val2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/host-groups/update)

---