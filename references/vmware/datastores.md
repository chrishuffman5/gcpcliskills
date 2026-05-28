# gcloud vmware datastores

manage VMware Engine datastores in Google Cloud VMware Engine

### `gcloud vmware datastores create`

Create a datastore

Create a datastore. Datastore creation is considered finished when the
datastore is in ACTIVE state. Check the progress of a datastore using
gcloud vmware datastores list.

**Synopsis:**
```
gcloud vmware datastores create (DATASTORE : --location=LOCATION)
    (--filestore=FILESTORE | --netapp=NETAPP
      | --third-party-nfs-file-share=THIRD_PARTY_NFS_FILE_SHARE
      --third-party-nfs-network=THIRD_PARTY_NFS_NETWORK
      --third-party-nfs-servers=SERVER,[SERVER,...]) [--async]
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datastore resource - datastore. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument datastore on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASTORE
     ID of the datastore or fully qualified identifier for the datastore.

     To set the datastore attribute:
     + provide the argument datastore on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument datastore on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filestore` | FILESTORE |  | _[Exactly one of these must be specified:]_ Google Filestore instance to be used as datastore. |
| `--netapp` | NETAPP |  | _[Exactly one of these must be specified:]_ Google NetApp volume to be used as datastore. |
| `--third-party-nfs-file-share` | THIRD_PARTY_NFS_FILE_SHARE |  | _[Exactly one of these must be specified:]_ Mount folder name of NFS. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--third-party-nfs-network` | THIRD_PARTY_NFS_NETWORK |  | _[Exactly one of these must be specified:]_ Network name of NFS's VPC. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--third-party-nfs-servers` | SERVER,[SERVER,...] |  | _[Exactly one of these must be specified:]_ Comma-separated list of server IP addresses of the NFS file service. This flag argument must be specified if any of the other arguments in this group are specified. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Text describing the datastore. |


**Examples:**
```bash
To create a datastore named my-datastore in us-west2-a connected to
filestore instance
projects/my-project/locations/us-west2-a/instances/my-filestore-instance,
run:

    $ gcloud vmware datastores create my-datastore \
        --location=us-west2-a --project=my-project \
        --filestore=projects/my-project/locations/us-west2-a/instances/\
    my-filestore-instance

Or:

    $ gcloud vmware datastores create my-datastore \
        --filestore=projects/my-project/locations/us-west2-a/instances/\
    my-filestore-instance

Or:

    $ gcloud vmware datastores create my-datastore \
        --netapp=projects/my-project/locations/us-west2-a/volumes/\
    my-netapp-volume

Or:

    $ gcloud vmware datastores create my-datastore \
        --third-party-nfs-network=my-network \
        --third-party-nfs-file-share=my-fileshare \
        --third-party-nfs-servers=10.0.0.1,10.0.0.2 \
        --location=us-west2-a --project=my-project

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/datastores/create)

---
### `gcloud vmware datastores delete`

Delete a datastore

Delete a datastore.

**Synopsis:**
```
gcloud vmware datastores delete (DATASTORE : --location=LOCATION) [--async]
    [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datastore resource - datastore. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument datastore on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASTORE
     ID of the datastore or fully qualified identifier for the datastore.

     To set the datastore attribute:
     + provide the argument datastore on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument datastore on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--etag` | ETAG |  | Etag of the datastore. |


**Examples:**
```bash
To delete a datastore named my-datastore in location us-west2-a, run:

    $ gcloud vmware datastores delete my-datastore \
        --location=us-west2-a --project=my-project

Or:

    $ gcloud vmware datastores delete my-datastore

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/datastores/delete)

---
### `gcloud vmware datastores describe`

Describe a datastore

Describe a datastore.

**Synopsis:**
```
gcloud vmware datastores describe (DATASTORE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datastore resource - datastore. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument datastore on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASTORE
     ID of the datastore or fully qualified identifier for the datastore.

     To set the datastore attribute:
     + provide the argument datastore on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument datastore on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To describe a datastore named my-datastore in location us-west2-a, run:

    $ gcloud vmware datastores describe my-datastore \
        --location=us-west2-a --project=my-project

Or:

    $ gcloud vmware datastores describe my-datastore

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/datastores/describe)

---
### `gcloud vmware datastores list`

List datastores

List datastores.

**Synopsis:**
```
gcloud vmware datastores list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list datastores in location us-west2-a, run:

    $ gcloud vmware datastores list --location=us-west2-a \
        --project=my-project

Or:

    $ gcloud vmware datastores list

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/datastores/list)

---
### `gcloud vmware datastores update`

Update a datastore

Update a datastore.

**Synopsis:**
```
gcloud vmware datastores update (DATASTORE : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datastore resource - datastore. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument datastore on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASTORE
     ID of the datastore or fully qualified identifier for the datastore.

     To set the datastore attribute:
     + provide the argument datastore on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument datastore on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | New description for the datastore. |


**Examples:**
```bash
To update a datastore named my-datastore in location us-west2-a with a new
description, run:

    $ gcloud vmware datastores update my-datastore \
        --location=us-west2-a --project=my-project \
        --description="new description"

Or:

    $ gcloud vmware datastores update my-datastore \
        --description="new description"

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/datastores/update)

---