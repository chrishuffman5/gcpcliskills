# gcloud bms nfs-shares

manage NFS shares in Bare Metal Solution

### `gcloud bms nfs-shares create`

Create a Bare Metal Solution NFS share

Create a Bare Metal Solution NFS share.

**Synopsis:**
```
gcloud bms nfs-shares create (NFS_SHARE : --region=REGION)
    --allowed-client=[PROPERTY=VALUE,...] --size-gib=SIZE_GIB
    --storage-type=STORAGE_TYPE [--async] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Nfs share resource - nfs_share. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument nfs_share on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NFS_SHARE
     ID of the nfs_share or fully qualified identifier for the nfs_share.

     To set the nfs_share attribute:
     + provide the argument nfs_share on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument nfs_share on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-client` | one of: READ_ONLY, READ_WRITE |  | Adds an allowed client to the NFS share. This flag can be repeated to specify multiple allowed clients. network The name of the network to allow. network-project-id The project ID of the allowed client network. If not present, the project ID of the NFS share will be used. cidr The subnet of IP addresses permitted to access the NFS share. mount-permissions The mount permissions for the allowed client. MOUNT_PERMISSIONS must be one of: READ_ONLY, READ_WRITE. allow-dev If yes, allows creation of devices. allow-suid If yes, allows SUID. enable-root-squash If yes, enables root squashing which is a special mapping of the remote superuser (root) identity when using identity authentication . |
| `--size-gib` | SIZE_GIB |  | The requested size of the NFS share in GiB |
| `--storage-type` | STORAGE_TYPE |  | Specifies the storage type of the underlying volume which will be created for the NFS share. STORAGE_TYPE must be one of: HDD The storage type of the underlying volume will be HDD SSD The storage type of the underlying volume will be SSD |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create an NFS share called my-share in region us-central1, with
requested size of 256 Gib, SSD storage and 2 allowed clients, run:

    $ gcloud bms nfs-shares create my-share --region=us-central1 \
        --size-gib=256 --storage-type=SSD \
        --allowed-client=network=my-network,\
    network-project-id=some-other-project,cidr=10.130.240.24/29,\
    mount-permissions=READ_ONLY,allow-dev=yes,allow-suid=no,\
    enable-root-squash=yes \
        --allowed-client=network=my-network2,cidr=10.130.240.26/28,\
    mount-permissions=READ_WRITE,allow-dev=yes,allow-suid=yes,\
    enable-root-squash=no
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/nfs-shares/create)

---
### `gcloud bms nfs-shares delete`

Delete a Bare Metal Solution NFS share

Delete a Bare Metal Solution NFS share.

**Synopsis:**
```
gcloud bms nfs-shares delete (NFS_SHARE : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Nfs share resource - nfs_share. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument nfs_share on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NFS_SHARE
     ID of the nfs_share or fully qualified identifier for the nfs_share.

     To set the nfs_share attribute:
     + provide the argument nfs_share on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument nfs_share on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an NFS share called my-share in region us-central1, run:

    $ gcloud bms nfs-shares delete my-share --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/nfs-shares/delete)

---
### `gcloud bms nfs-shares describe`

Describe a Bare Metal solution NFS share

Describe a Bare Metal Solution NFS share.

**Synopsis:**
```
gcloud bms nfs-shares describe (NFS_SHARE : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Nfs share resource - nfs_share. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument nfs_share on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NFS_SHARE
     ID of the nfs_share or fully qualified identifier for the nfs_share.

     To set the nfs_share attribute:
     + provide the argument nfs_share on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument nfs_share on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To get a description of an NFS share called my-nfs-share in project
my-project and region us-central1, run:

    $ gcloud bms nfs-shares describe my-nfs-share --project=my-project \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/nfs-shares/describe)

---
### `gcloud bms nfs-shares list`

List Bare Metal Solution NFS shares in a project

List Bare Metal Solution NFS shares in a project.

**Synopsis:**
```
gcloud bms nfs-shares list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list NFS shares within the project in the region us-central1, run:

    $ gcloud bms nfs-shares list --region=us-central1

Or:

To list all NFS shares in the project, run:

    $ gcloud bms nfs-shares list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/nfs-shares/list)

---
### `gcloud bms nfs-shares rename`

Rename a Bare Metal Solution nfs-share

Rename a Bare Metal Solution nfs-share.

**Synopsis:**
```
gcloud bms nfs-shares rename (NFS_SHARE : --region=REGION)
    --new-name=NEW_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Nfs share resource - nfs_share. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument nfs_share on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NFS_SHARE
     ID of the nfs_share or fully qualified identifier for the nfs_share.

     To set the nfs_share attribute:
     + provide the argument nfs_share on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument nfs_share on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--new-name` | NEW_NAME |  | New nfs-share name for renaming an already existing nfs-share. |


**Examples:**
```bash
To rename a nfs-share my-nfs-share to my-new-nfs-share-name in region
us-central1, run:

    $ gcloud bms nfs-shares rename my-nfs-share \
        --new-name=my-new-nfs-share-name --region=us-central1 \
        --project=bms-example-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/nfs-shares/rename)

---
### `gcloud bms nfs-shares update`

Update a Bare Metal Solution NFS share

Update a Bare Metal Solution NFS share.

This call returns immediately, but the update operation may take several
minutes to complete. To check if the operation is complete, use the
describe command for the NFS share.

**Synopsis:**
```
gcloud bms nfs-shares update (NFS_SHARE : --region=REGION) [--async]
    [--update-labels=[KEY=VALUE,...]]
    [--add-allowed-client=[PROPERTY=VALUE,...] | --clear-allowed-clients
      | --remove-allowed-client=[PROPERTY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Nfs share resource - nfs_share. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument nfs_share on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NFS_SHARE
     ID of the nfs_share or fully qualified identifier for the nfs_share.

     To set the nfs_share attribute:
     + provide the argument nfs_share on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument nfs_share on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update an NFS share called my-share in region us-central1 with a new
label key1=value1, run:

    $ gcloud bms nfs-shares update my-share --region=us-central1 \
        --update-labels=key1=value1

To clear all labels, run:

    $ gcloud bms nfs-shares update my-share --region=us-central1 \
        --clear-labels

To remove label key1, run:

    $ gcloud bms nfs-shares update my-share --region=us-central1 \
        --remove-labels=key1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/nfs-shares/update)

---