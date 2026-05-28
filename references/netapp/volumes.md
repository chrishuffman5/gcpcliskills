# gcloud netapp volumes

create and manage Cloud NetApp Volumes

### `gcloud netapp volumes create`

Create a Cloud NetApp Volume

**Synopsis:**
```
gcloud netapp volumes create (VOLUME : --location=LOCATION)
    --capacity=CAPACITY --protocols=PROTOCOL,[PROTOCOL,...]
    --storage-pool=STORAGE_POOL [--async]
    [--backup-config=[backup-policies=BACKUP-POLICIES],
      [backup-vault=BACKUP-VAULT],
      [enable-scheduled-backups=ENABLE-SCHEDULED-BACKUPS]]
    [--block-devices=[host-groups=HOST-GROUPS],
      [name=NAME],[os-type=OS-TYPE],[size-gib=SIZE-GIB]]
    [--cache-parameters=[cache-config=CACHE-CONFIG],
      [enable-global-file-lock=ENABLE-GLOBAL-FILE-LOCK],
      [peer-cluster-name=PEER-CLUSTER-NAME],
      [peer-ip-addresses=PEER-IP-ADDRESSES],
      [peer-svm-name=PEER-SVM-NAME],[peer-volume-name=PEER-VOLUME-NAME]]
    [--cache-pre-populate=[exclude-path-list=EXCLUDE-PATH-LIST],
      [path-list=PATH-LIST],[recursion=RECURSION]]
    [--description=DESCRIPTION] [--enable-kerberos=ENABLE_KERBEROS]
    [--export-policy=[access-type=ACCESS-TYPE],
      [allowed-clients=ALLOWED-CLIENTS],[anon-uid=ANON-UID],
      [has-root-access=HAS-ROOT-ACCESS],
      [kerberos-5-read-only=KERBEROS-5-READ-ONLY],
      [kerberos-5-read-write=KERBEROS-5-READ-WRITE],
      [kerberos-5i-read-only=KERBEROS-5I-READ-ONLY],
      [kerberos-5i-read-write=KERBEROS-5I-READ-WRITE],
      [kerberos-5p-read-only=KERBEROS-5P-READ-ONLY],
      [kerberos-5p-read-write=KERBEROS-5P-READ-WRITE],
      [nfsv3=NFSV3],[nfsv4=NFSV4],[squash-mode=SQUASH-MODE]]
    [--hybrid-replication-parameters=[cluster-location=CLUSTER-LOCATION],
      [description=DESCRIPTION],
      [hybrid-replication-type=HYBRID-REPLICATION-TYPE],[labels=LABELS],
      [large-volume-constituent-count=LARGE-VOLUME-CONSTITUENT-COUNT],
      [peer-cluster-name=PEER-CLUSTER-NAME],
      [peer-ip-addresses=PEER-IP-ADDRESSES],[peer-svm-name=PEER-SVM-NAME],
      [peer-volume-name=PEER-VOLUME-NAME],[replication=REPLICATION],
      [replication-schedule=REPLICATION-SCHEDULE]]
    [--labels=[KEY=VALUE,...]] [--large-capacity=LARGE_CAPACITY]
    [--multiple-endpoints=MULTIPLE_ENDPOINTS]
    [--restricted-actions=RESTRICTED_ACTION,[...]]
    [--security-style=SECURITY_STYLE; default="SECURITY_STYLE_UNSPECIFIED"]
    [--share-name=SHARE_NAME]
    [--smb-settings=SMB_SETTING,[SMB_SETTING,...]]
    [--snap-reserve=SNAP_RESERVE]
    [--snapshot-daily=[hour=HOUR],
      [minute=MINUTE],[snapshots-to-keep=SNAPSHOTS-TO-KEEP]]
    [--snapshot-directory=SNAPSHOT_DIRECTORY; default="true"]
    [--snapshot-hourly=[minute=MINUTE],
      [snapshots-to-keep=SNAPSHOTS-TO-KEEP]]
    [--snapshot-monthly=[day=DAY],
      [hour=HOUR],[minute=MINUTE],[snapshots-to-keep=SNAPSHOTS-TO-KEEP]]
    [--snapshot-weekly=[day=DAY],
      [hour=HOUR],[minute=MINUTE],[snapshots-to-keep=SNAPSHOTS-TO-KEEP]]
    [--source-snapshot=SOURCE_SNAPSHOT]
    [--throughput-mibps=THROUGHPUT_MIBPS]
    [--tiering-policy=[tier-action=ENABLED|PAUSED,...]]
    [--unix-permissions=UNIX_PERMISSIONS]
    [--source-backup=SOURCE_BACKUP : --backup_vault=BACKUP_VAULT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Volume resource - The Volume to create. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument volume on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VOLUME
     ID of the volume or fully qualified identifier for the volume.

     To set the volume attribute:
     + provide the argument volume on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the volume.

     To set the location attribute:
     + provide the argument volume on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--capacity` | CAPACITY |  | The desired capacity of the Volume in GiB or TiB units.If no capacity unit is specified, GiB is assumed. |
| `--protocols` | PROTOCOL,[PROTOCOL,...] |  | Type of File System protocols for the Cloud NetApp Files Volume. Valid component values are: NFSV3, NFSV4, SMB. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--backup-config` | [backup-policies=BACKUP-POLICIES],[backup-vault=BACKUP-VAULT],[enable-scheduled-backups=ENABLE-SCHEDULED-BACKUPS] |  | Backup Config contains backup related config on a volume. Backup Config will have the following format `--backup-config=backup-policies=BACKUP_POLICIES, backup-vault=BACKUP_VAULT_NAME, enable-scheduled-backups=ENABLE_SCHEDULED_BACKUPS backup-policies is a pound-separated (#) list of backup policy names, backup-vault can include a single backup-vault resource name, and enable-scheduled-backups is a Boolean value indicating whether or not scheduled backups are enabled on the volume. |
| `--block-devices` | [host-groups=HOST-GROUPS],[name=NAME],[os-type=OS-TYPE],[size-gib=SIZE-GIB] |  | A block device to be created with the volume. This flag can be repeated to specify multiple block devices. The following keys are available: name A user-defined name for the block device. host-groups A comma-separated list of host groups that can mount the block volume. os-type The OS type of the volume. Allowed values are OS_TYPE_UNSPECIFIED, LINUX, WINDOWS. size-gib The size of the block device in GiB. Note that this value is ignored during volume creation and is system-managed. |
| `--cache-parameters` | [cache-config=CACHE-CONFIG],[enable-global-file-lock=ENABLE-GLOBAL-FILE-LOCK],[peer-cluster-name=PEER-CLUSTER-NAME],[peer-ip-addresses=PEER-IP-ADDRESSES],[peer-svm-name=PEER-SVM-NAME],[peer-volume-name=PEER-VOLUME-NAME] |  | Cache Parameters contains cache parameters of a volume. Cache Parameters will have the following format `--cache-parameters=peer-volume-name=PEER_VOLUME_NAME, peer-cluster-name=PEER_CLUSTER_NAME, peer-svm-name=PEER_SVM_NAME, peer-ip-addresses=[PEER-IP-ADDRESS1#PEER-IP-ADDRESS2#...], enable-global-file-lock=ENABLE_GLOBAL_FILE_LOCK, cache-config=CACHE_CONFIG` *peer-volume-name*::: Name of the user's local source volume *peer-cluster-name*::: Name of the user's local source cluster *peer-svm-name*::: Name of the user's local source vserver svm *peer-ip-addresses*::: Hashtag-separated(#) list of IP addresses *enable-global-file-lock*::: If true, enable global file lock *cache-config*::: Cache-config as a hashtag-separated(#) list of key-value pairs |
| `--cache-pre-populate` | [exclude-path-list=EXCLUDE-PATH-LIST],[path-list=PATH-LIST],[recursion=RECURSION] |  | Cache Pre-populate contains cache pre-populate parameters of a volume. Cache Pre-populate will have the following format --cache-pre-populate=path-list=PATH_LIST1#PATH_LIST2, exclude-path-list=EXCLUDE_PATH_LIST1#EXCLUDE_PATH_LIST2, recursion=RECURSION path-list Hashtag-separated(#) list of paths to be pre-populated exclude-path-list Hashtag-separated(#) list of paths to be excluded from pre-population recursion Boolean value indicating pre-populate recursion. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Volume |
| `--enable-kerberos` | ENABLE_KERBEROS |  | Boolean flag indicating whether Volume is a kerberos Volume or not |
| `--export-policy` | [access-type=ACCESS-TYPE],[allowed-clients=ALLOWED-CLIENTS],[anon-uid=ANON-UID],[has-root-access=HAS-ROOT-ACCESS],[kerberos-5-read-only=KERBEROS-5-READ-ONLY],[kerberos-5-read-write=KERBEROS-5-READ-WRITE],[kerberos-5i-read-only=KERBEROS-5I-READ-ONLY],[kerberos-5i-read-write=KERBEROS-5I-READ-WRITE],[kerberos-5p-read-only=KERBEROS-5P-READ-ONLY],[kerberos-5p-read-write=KERBEROS-5P-READ-WRITE],[nfsv3=NFSV3],[nfsv4=NFSV4],[squash-mode=SQUASH-MODE] |  | Export Policy of a Cloud NetApp Files Volume. This will be a field similar to network in which export policy fields can be specified as such: --export-policy=allowed-clients=ALLOWED_CLIENTS_IP_ADDRESSES, has-root-access=HAS_ROOT_ACCESS_BOOL,access=ACCESS_TYPE,nfsv3=NFSV3, nfsv4=NFSV4,kerberos-5-read-only=KERBEROS_5_READ_ONLY, kerberos-5-read-write=KERBEROS_5_READ_WRITE, kerberos-5i-read-only=KERBEROS_5I_READ_ONLY, kerberos-5i-read-write=KERBEROS_5I_READ_WRITE, kerberos-5p-read-only=KERBEROS_5P_READ_ONLY, kerberos-5p-read-write=KERBEROS_5P_READ_WRITE, squash-mode=SQUASH_MODE,anon-uid=ANON_UID |
| `--hybrid-replication-parameters` | [cluster-location=CLUSTER-LOCATION],[description=DESCRIPTION],[hybrid-replication-type=HYBRID-REPLICATION-TYPE],[labels=LABELS],[large-volume-constituent-count=LARGE-VOLUME-CONSTITUENT-COUNT],[peer-cluster-name=PEER-CLUSTER-NAME],[peer-ip-addresses=PEER-IP-ADDRESSES],[peer-svm-name=PEER-SVM-NAME],[peer-volume-name=PEER-VOLUME-NAME],[replication=REPLICATION],[replication-schedule=REPLICATION-SCHEDULE] |  | Hybrid Replication Parameters contains hybrid replication parameters on a volume. Hybrid Replication Parameters will have the following format --hybrid-replication-parameters=replication=REPLICATION, peer-volume-name=PEER_VOLUME_NAME, peer-cluster-name=PEER_CLUSTER_NAME, peer-svm-name=PEER_SVM_NAME, peer-ip-addresses=[PEER-IP-ADDRESS1#PEER-IP-ADDRESS2#...], cluster-location=CLUSTER_LOCATION, description=DESCRIPTION, replication-schedule=REPLICATION_SCHEDULE, hybrid-replication-type=HYBRID_REPLICATION_TYPE, large-volume-constituent-count=LARGE_VOLUME_CONSTITUENT_COUNT, labels=[KEY1:VALUE1#KEY2:VALUE2#...], replication is the desired name for the replication of the volume, peer-volume-name is the name of the user's local source volume, peer-cluster-name is the name of the user's local source cluster, peer-svm-name is the name of the user's local source vserver svm, peer-ip-addresses is a ampersand-separated(#) list of ip addresses, cluster-location is the name of the source cluster location, description is the description of the replication, replication-schedule is the schedule of corresponding hybrid replication created, hybrid-replication-type is the hybrid replication type of the corresponding hybrid replication created, large-volume-constituent-count is the number of constituent volumes in the large volume, and labels is an hashtag-separated(#) key value pair of labels with key and value separated by colon(:) for the replication. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--large-capacity` | LARGE_CAPACITY |  | Boolean flag indicating whether Volume is a large capacity Volume or not |
| `--multiple-endpoints` | MULTIPLE_ENDPOINTS |  | Boolean flag indicating whether Volume is a multiple endpoints Volume or not |
| `--restricted-actions` | RESTRICTED_ACTION,[...] |  | Actions to be restricted for a volume. Valid restricted action options are: 'DELETE'. |
| `--security-style` | one of: ntfs NTFS security style for Volume | SECURITY_STYLE_UNSPECIFIED | The security style of the Volume. This can either be UNIX or NTFS. SECURITY_STYLE must be one of: ntfs NTFS security style for Volume. unix UNIX security style for Volume |
| `--share-name` | SHARE_NAME |  | Share name of the Mount path clients will use. |
| `--smb-settings` | SMB_SETTING,[SMB_SETTING,...] |  | List of settings specific to SMB protocol for a Cloud NetApp Files Volume. Valid component values are: ENCRYPT_DATA, BROWSABLE, CHANGE_NOTIFY, NON_BROWSABLE, OPLOCKS, SHOW_SNAPSHOT, SHOW_PREVIOUS_VERSIONS, ACCESS_BASED_ENUMERATION, CONTINUOUSLY_AVAILABLE. |
| `--snap-reserve` | SNAP_RESERVE |  | (DEPRECATED) The percentage of volume storage reserved for snapshot storage. The default value for this is 0 percent The snap-reserve option is deprecated |
| `--snapshot-daily` | [hour=HOUR],[minute=MINUTE],[snapshots-to-keep=SNAPSHOTS-TO-KEEP] |  | Make a snapshot every day e.g. at 06:00, 05:20, 23:50 |
| `--snapshot-directory` | SNAPSHOT_DIRECTORY | true | Snapshot Directory if enabled (true) makes the Volume contain a read-only .snapshot directory which provides access to each of the volume's snapshots |
| `--snapshot-hourly` | [minute=MINUTE],[snapshots-to-keep=SNAPSHOTS-TO-KEEP] |  | Make a snapshot every hour e.g. at 04:00, 05:20, 06:00 |
| `--snapshot-monthly` | [day=DAY],[hour=HOUR],[minute=MINUTE],[snapshots-to-keep=SNAPSHOTS-TO-KEEP] |  | Make a snapshot once a month e.g. at 2nd 04:00, 7th 05:20, 24th 23:50 |
| `--snapshot-weekly` | [day=DAY],[hour=HOUR],[minute=MINUTE],[snapshots-to-keep=SNAPSHOTS-TO-KEEP] |  | Make a snapshot every week e.g. at Monday 04:00, Wednesday 05:20, Sunday 23:50 |
| `--throughput-mibps` | THROUGHPUT_MIBPS |  | _[+ provide the argument --source-snapshot on the command line.]_ The desired throughput of the volume in MiB/s. |
| `--tiering-policy` | [tier-action=ENABLED\|PAUSED,...] |  | _[+ provide the argument --source-snapshot on the command line.]_ Tiering Policy contains auto tiering policy on a volume. Tiering Policy will have the following format --tiering-policy=tier-action=TIER_ACTION, cooling-threshold-days=COOLING_THRESHOLD_DAYS tier-action is an enum, supported values are ENABLED or PAUSED, cooling-threshold-days is an integer represents time in days to mark the volume's data block as cold and make it eligible for tiering, can be range from 7-183. Default is 31. |
| `--unix-permissions` | UNIX_PERMISSIONS |  | _[+ provide the argument --source-snapshot on the command line.]_ Unix permissions the mount point will be created with. Unix permissions are only applicable with NFS protocol only |


**Examples:**
```bash
The following command creates a NFS Volume named NAME asynchronously using
the specified arguments

    $ gcloud netapp volumes create NAME --capacity=1024 \
      --protocols=nfsv3,nfsv4 --share-name=share1 --storage-pool=sp1 \
      --description="test description" --enable-kerberos=true \
      --unix-permissions=0755 --async

The following command creates a SMB Volume named NAME asynchronously using
the specified arguments

    $ gcloud netapp volumes create NAME --capacity=1024 \
      --protocols=smb --share-name=share2 --storage-pool=sp2 \
      --description="test smb" --security-style=ntfs \
      --smb-settings=SHOW_SNAPSHOT,SHOW_PREVIOUS_VERSIONS,\
    ACCESS_BASED_ENUMERATION --snap-reserve=0.1 --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/create)

---
### `gcloud netapp volumes delete`

Delete a Cloud NetApp Volume

**Synopsis:**
```
gcloud netapp volumes delete (VOLUME : --location=LOCATION) [--async]
    [--force] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Volume resource - The Volume to delete. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument volume on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VOLUME
     ID of the volume or fully qualified identifier for the volume.

     To set the volume attribute:
     + provide the argument volume on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the volume.

     To set the location attribute:
     + provide the argument volume on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | Forces the deletion of a volume and its child resources, such as snapshots. |


**Examples:**
```bash
The following command deletes a Volume named NAME in the given location

    $ gcloud netapp volumes delete NAME --location=us-central1

To delete a Volume named NAME asynchronously, run the following command:

    $ gcloud netapp volumes delete NAME --location=us-central1 --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/delete)

---
### `gcloud netapp volumes describe`

Show metadata for a Cloud NetApp Volume

Describe a Cloud NetApp Volume

**Synopsis:**
```
gcloud netapp volumes describe (VOLUME : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Volume resource - The Volume to describe. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument volume on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VOLUME
     ID of the volume or fully qualified identifier for the volume.

     To set the volume attribute:
     + provide the argument volume on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the volume.

     To set the location attribute:
     + provide the argument volume on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Examples:**
```bash
The following command describe a Volume named NAME in the given location

    $ gcloud netapp volumes describe NAME --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/describe)

---
### `gcloud netapp volumes list`

List Cloud NetApp Volumes

Lists Cloud NetApp Volumes

**Synopsis:**
```
gcloud netapp volumes list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + uses all locations by default.; + set the property netapp/location. |


**Examples:**
```bash
The following command lists all Volumes in the given location

    $ gcloud netapp volumes list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/list)

---
### `gcloud netapp volumes restore-backup-files`

Restore specific files from a backup to a Volume

**Synopsis:**
```
gcloud netapp volumes restore-backup-files (VOLUME : --location=LOCATION)
    --file-list=FILE_LIST,[FILE_LIST,...]
    (--backup=BACKUP : --backup_vault=BACKUP_VAULT) [--async]
    [--restore-destination-path=RESTORE_DESTINATION_PATH]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Volume resource - The Volume to restore into. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument volume on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VOLUME
     ID of the volume or fully qualified identifier for the volume.

     To set the volume attribute:
     + provide the argument volume on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the volume.

     To set the location attribute:
     + provide the argument volume on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file-list` | FILE_LIST,[FILE_LIST,...] |  | List of files to be restored in the form of their absolute path as in source volume. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--restore-destination-path` | RESTORE_DESTINATION_PATH |  | Name of the absolute directory path in the destination volume.. |


**Examples:**
```bash
The following command restores file1.txt and file2.txt from the given
backup to a Volume named NAME to the directory
/path/to/destination/directory.

    $ gcloud netapp volumes restore-backup-files NAME \
      --location=us-central1 --backup=backup-1 \
      --file-list=file1.txt,file2.txt \
      --restore-destination-path=/path/to/destination/directory
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/restore-backup-files)

---
### `gcloud netapp volumes revert`

Revert a Cloud NetApp Volume back to a specified Snapshot

Revert a Cloud NetApp Volume back to a specified source Snapshot

**Synopsis:**
```
gcloud netapp volumes revert (VOLUME : --location=LOCATION)
    --snapshot=SNAPSHOT [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Volume resource - The Volume to revert. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument volume on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VOLUME
     ID of the volume or fully qualified identifier for the volume.

     To set the volume attribute:
     + provide the argument volume on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the volume.

     To set the location attribute:
     + provide the argument volume on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--snapshot` | SNAPSHOT |  | _[This must be specified.]_ ID of the snapshot or fully qualified identifier for the snapshot. To set the snapshot attribute: + provide the argument --snapshot on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command reverts a Volume named NAME in the given location and
snapshot

    $ gcloud netapp volumes revert NAME --location=us-central1 \
      --snapshot="snapshot1"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/revert)

---
### `gcloud netapp volumes update`

Update a Cloud NetApp Volume

Update a Cloud NetApp Volume and its specified parameters

**Synopsis:**
```
gcloud netapp volumes update (VOLUME : --location=LOCATION) [--async]
    [--backup-config=[backup-policies=BACKUP-POLICIES],
      [backup-vault=BACKUP-VAULT],
      [enable-scheduled-backups=ENABLE-SCHEDULED-BACKUPS]]
    [--block-devices=[host-groups=HOST-GROUPS],
      [name=NAME],[os-type=OS-TYPE],[size-gib=SIZE-GIB]]
    [--cache-parameters=[cache-config=CACHE-CONFIG],
      [enable-global-file-lock=ENABLE-GLOBAL-FILE-LOCK],
      [peer-cluster-name=PEER-CLUSTER-NAME],
      [peer-ip-addresses=PEER-IP-ADDRESSES],
      [peer-svm-name=PEER-SVM-NAME],[peer-volume-name=PEER-VOLUME-NAME]]
    [--cache-pre-populate=[exclude-path-list=EXCLUDE-PATH-LIST],
      [path-list=PATH-LIST],[recursion=RECURSION]] [--capacity=CAPACITY]
    [--description=DESCRIPTION] [--enable-kerberos=ENABLE_KERBEROS]
    [--export-policy=[access-type=ACCESS-TYPE],
      [allowed-clients=ALLOWED-CLIENTS],[anon-uid=ANON-UID],
      [has-root-access=HAS-ROOT-ACCESS],
      [kerberos-5-read-only=KERBEROS-5-READ-ONLY],
      [kerberos-5-read-write=KERBEROS-5-READ-WRITE],
      [kerberos-5i-read-only=KERBEROS-5I-READ-ONLY],
      [kerberos-5i-read-write=KERBEROS-5I-READ-WRITE],
      [kerberos-5p-read-only=KERBEROS-5P-READ-ONLY],
      [kerberos-5p-read-write=KERBEROS-5P-READ-WRITE],
      [nfsv3=NFSV3],[nfsv4=NFSV4],[squash-mode=SQUASH-MODE]]
    [--protocols=PROTOCOL,[PROTOCOL,...]]
    [--restricted-actions=RESTRICTED_ACTION,[...]]
    [--security-style=SECURITY_STYLE; default="SECURITY_STYLE_UNSPECIFIED"]
    [--share-name=SHARE_NAME]
    [--smb-settings=SMB_SETTING,[SMB_SETTING,...]]
    [--snap-reserve=SNAP_RESERVE]
    [--snapshot-daily=[hour=HOUR],
      [minute=MINUTE],[snapshots-to-keep=SNAPSHOTS-TO-KEEP]]
    [--snapshot-directory=SNAPSHOT_DIRECTORY; default="true"]
    [--snapshot-hourly=[minute=MINUTE],
      [snapshots-to-keep=SNAPSHOTS-TO-KEEP]]
    [--snapshot-monthly=[day=DAY],
      [hour=HOUR],[minute=MINUTE],[snapshots-to-keep=SNAPSHOTS-TO-KEEP]]
    [--snapshot-weekly=[day=DAY],
      [hour=HOUR],[minute=MINUTE],[snapshots-to-keep=SNAPSHOTS-TO-KEEP]]
    [--source-snapshot=SOURCE_SNAPSHOT] [--storage-pool=STORAGE_POOL]
    [--throughput-mibps=THROUGHPUT_MIBPS]
    [--tiering-policy=[tier-action=ENABLED|PAUSED,...]]
    [--unix-permissions=UNIX_PERMISSIONS] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--source-backup=SOURCE_BACKUP : --backup_vault=BACKUP_VAULT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Volume resource - The Volume to update. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument volume on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VOLUME
     ID of the volume or fully qualified identifier for the volume.

     To set the volume attribute:
     + provide the argument volume on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the volume.

     To set the location attribute:
     + provide the argument volume on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--backup-config` | [backup-policies=BACKUP-POLICIES],[backup-vault=BACKUP-VAULT],[enable-scheduled-backups=ENABLE-SCHEDULED-BACKUPS] |  | Backup Config contains backup related config on a volume. Backup Config will have the following format `--backup-config=backup-policies=BACKUP_POLICIES, backup-vault=BACKUP_VAULT_NAME, enable-scheduled-backups=ENABLE_SCHEDULED_BACKUPS backup-policies is a pound-separated (#) list of backup policy names, backup-vault can include a single backup-vault resource name, and enable-scheduled-backups is a Boolean value indicating whether or not scheduled backups are enabled on the volume. |
| `--block-devices` | [host-groups=HOST-GROUPS],[name=NAME],[os-type=OS-TYPE],[size-gib=SIZE-GIB] |  | A block device to be created with the volume. This flag can be repeated to specify multiple block devices. The following keys are available: name A user-defined name for the block device. host-groups A comma-separated list of host groups that can mount the block volume. os-type The OS type of the volume. Allowed values are OS_TYPE_UNSPECIFIED, LINUX, WINDOWS. size-gib The size of the block device in GiB. Note that this value is ignored during volume creation and is system-managed. |
| `--cache-parameters` | [cache-config=CACHE-CONFIG],[enable-global-file-lock=ENABLE-GLOBAL-FILE-LOCK],[peer-cluster-name=PEER-CLUSTER-NAME],[peer-ip-addresses=PEER-IP-ADDRESSES],[peer-svm-name=PEER-SVM-NAME],[peer-volume-name=PEER-VOLUME-NAME] |  | Cache Parameters contains cache parameters of a volume. Cache Parameters will have the following format `--cache-parameters=peer-volume-name=PEER_VOLUME_NAME, peer-cluster-name=PEER_CLUSTER_NAME, peer-svm-name=PEER_SVM_NAME, peer-ip-addresses=[PEER-IP-ADDRESS1#PEER-IP-ADDRESS2#...], enable-global-file-lock=ENABLE_GLOBAL_FILE_LOCK, cache-config=CACHE_CONFIG` *peer-volume-name*::: Name of the user's local source volume *peer-cluster-name*::: Name of the user's local source cluster *peer-svm-name*::: Name of the user's local source vserver svm *peer-ip-addresses*::: Hashtag-separated(#) list of IP addresses *enable-global-file-lock*::: If true, enable global file lock *cache-config*::: Cache-config as a hashtag-separated(#) list of key-value pairs |
| `--cache-pre-populate` | [exclude-path-list=EXCLUDE-PATH-LIST],[path-list=PATH-LIST],[recursion=RECURSION] |  | Cache Pre-populate contains cache pre-populate parameters of a volume. Cache Pre-populate will have the following format --cache-pre-populate=path-list=PATH_LIST1#PATH_LIST2, exclude-path-list=EXCLUDE_PATH_LIST1#EXCLUDE_PATH_LIST2, recursion=RECURSION path-list Hashtag-separated(#) list of paths to be pre-populated exclude-path-list Hashtag-separated(#) list of paths to be excluded from pre-population recursion Boolean value indicating pre-populate recursion. |
| `--capacity` | CAPACITY |  | The desired capacity of the Volume in GiB or TiB units.If no capacity unit is specified, GiB is assumed. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Volume |
| `--enable-kerberos` | ENABLE_KERBEROS |  | Boolean flag indicating whether Volume is a kerberos Volume or not |
| `--export-policy` | [access-type=ACCESS-TYPE],[allowed-clients=ALLOWED-CLIENTS],[anon-uid=ANON-UID],[has-root-access=HAS-ROOT-ACCESS],[kerberos-5-read-only=KERBEROS-5-READ-ONLY],[kerberos-5-read-write=KERBEROS-5-READ-WRITE],[kerberos-5i-read-only=KERBEROS-5I-READ-ONLY],[kerberos-5i-read-write=KERBEROS-5I-READ-WRITE],[kerberos-5p-read-only=KERBEROS-5P-READ-ONLY],[kerberos-5p-read-write=KERBEROS-5P-READ-WRITE],[nfsv3=NFSV3],[nfsv4=NFSV4],[squash-mode=SQUASH-MODE] |  | Export Policy of a Cloud NetApp Files Volume. This will be a field similar to network in which export policy fields can be specified as such: --export-policy=allowed-clients=ALLOWED_CLIENTS_IP_ADDRESSES, has-root-access=HAS_ROOT_ACCESS_BOOL,access=ACCESS_TYPE,nfsv3=NFSV3, nfsv4=NFSV4,kerberos-5-read-only=KERBEROS_5_READ_ONLY, kerberos-5-read-write=KERBEROS_5_READ_WRITE, kerberos-5i-read-only=KERBEROS_5I_READ_ONLY, kerberos-5i-read-write=KERBEROS_5I_READ_WRITE, kerberos-5p-read-only=KERBEROS_5P_READ_ONLY, kerberos-5p-read-write=KERBEROS_5P_READ_WRITE, squash-mode=SQUASH_MODE,anon-uid=ANON_UID |
| `--protocols` | PROTOCOL,[PROTOCOL,...] |  | Type of File System protocols for the Cloud NetApp Files Volume. Valid component values are: NFSV3, NFSV4, SMB. |
| `--restricted-actions` | RESTRICTED_ACTION,[...] |  | Actions to be restricted for a volume. Valid restricted action options are: 'DELETE'. |
| `--security-style` | one of: ntfs NTFS security style for Volume | SECURITY_STYLE_UNSPECIFIED | The security style of the Volume. This can either be UNIX or NTFS. SECURITY_STYLE must be one of: ntfs NTFS security style for Volume. unix UNIX security style for Volume |
| `--share-name` | SHARE_NAME |  | Share name of the Mount path clients will use. |
| `--smb-settings` | SMB_SETTING,[SMB_SETTING,...] |  | List of settings specific to SMB protocol for a Cloud NetApp Files Volume. Valid component values are: ENCRYPT_DATA, BROWSABLE, CHANGE_NOTIFY, NON_BROWSABLE, OPLOCKS, SHOW_SNAPSHOT, SHOW_PREVIOUS_VERSIONS, ACCESS_BASED_ENUMERATION, CONTINUOUSLY_AVAILABLE. |
| `--snap-reserve` | SNAP_RESERVE |  | (DEPRECATED) The percentage of volume storage reserved for snapshot storage. The default value for this is 0 percent The snap-reserve option is deprecated |
| `--snapshot-daily` | [hour=HOUR],[minute=MINUTE],[snapshots-to-keep=SNAPSHOTS-TO-KEEP] |  | Make a snapshot every day e.g. at 06:00, 05:20, 23:50 |
| `--snapshot-directory` | SNAPSHOT_DIRECTORY | true | Snapshot Directory if enabled (true) makes the Volume contain a read-only .snapshot directory which provides access to each of the volume's snapshots |
| `--snapshot-hourly` | [minute=MINUTE],[snapshots-to-keep=SNAPSHOTS-TO-KEEP] |  | Make a snapshot every hour e.g. at 04:00, 05:20, 06:00 |
| `--snapshot-monthly` | [day=DAY],[hour=HOUR],[minute=MINUTE],[snapshots-to-keep=SNAPSHOTS-TO-KEEP] |  | Make a snapshot once a month e.g. at 2nd 04:00, 7th 05:20, 24th 23:50 |
| `--snapshot-weekly` | [day=DAY],[hour=HOUR],[minute=MINUTE],[snapshots-to-keep=SNAPSHOTS-TO-KEEP] |  | Make a snapshot every week e.g. at Monday 04:00, Wednesday 05:20, Sunday 23:50 |
| `--throughput-mibps` | THROUGHPUT_MIBPS |  | _[+ provide the argument --storage-pool on the command line.]_ The desired throughput of the volume in MiB/s. |
| `--tiering-policy` | [tier-action=ENABLED\|PAUSED,...] |  | _[+ provide the argument --storage-pool on the command line.]_ Tiering Policy contains auto tiering policy on a volume. Tiering Policy will have the following format --tiering-policy=tier-action=TIER_ACTION, cooling-threshold-days=COOLING_THRESHOLD_DAYS tier-action is an enum, supported values are ENABLED or PAUSED, cooling-threshold-days is an integer represents time in days to mark the volume's data block as cold and make it eligible for tiering, can be range from 7-183. Default is 31. |
| `--unix-permissions` | UNIX_PERMISSIONS |  | _[+ provide the argument --storage-pool on the command line.]_ Unix permissions the mount point will be created with. Unix permissions are only applicable with NFS protocol only |
| `--update-labels` | [KEY=VALUE,...] |  | _[+ provide the argument --storage-pool on the command line.]_ List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command updates a Volume named NAME and its specified
parameters

    $ gcloud netapp volumes update NAME --location=us-central1 \
      --capacity=4096 --description="new description" \
      --enable-kerberos=false --storage-pool=sp3 \
      --unix-permissions=0777
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/update)

---

## `gcloud netapp volumes quota-rules` — create and manage Cloud NetApp Volume QuotaRules
### `gcloud netapp volumes quota-rules create`

Create a Cloud NetApp Volume Quota Rule

Create a Cloud NetApp Volume Quota Rule.

**Synopsis:**
```
gcloud netapp volumes quota-rules create (QUOTA_RULE : --location=LOCATION)
    --disk-limit-mib=DISK_LIMIT_MIB --type=TYPE [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--target=TARGET] [--volume=VOLUME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Quota rule resource - The Quota rule to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument quota_rule on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument quota_rule on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  QUOTA_RULE
     ID of the quota_rule or fully qualified identifier for the
     quota_rule.

     To set the quota_rule attribute:
     + provide the argument quota_rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the quota_rule.

     To set the location attribute:
     + provide the argument quota_rule on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--disk-limit-mib` | DISK_LIMIT_MIB |  | The disk limit in MiB for the quota rule. |
| `--type` | TYPE |  | String indicating the type of quota rule. The supported values are: 'DEFAULT_USER_QUOTA','DEFAULT_GROUP_QUOTA','INDIVIDUAL_USER_QUOTA','INDIVIDUAL_GROUP_QUOTA' |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Quota rule |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--target` | TARGET |  | The target of the quota rule. Identified by a Unix UID/GID, Windows SID, or null for default. |


**Examples:**
```bash
The following command creates a default user Quota Rule named NAME using
the required arguments:

    $ gcloud netapp volumes quota-rules create NAME \
      --location=us-central1 --volume=vol1 --type=DEFAULT_USER_QUOTA \
      --disk-limit-mib=200

The following command creates a default group Quota Rule named NAME using
the required arguments:

    $ gcloud netapp volumes quota-rules create NAME \
      --location=us-central1 --volume=vol1 \
      --type=DEFAULT_GROUP_QUOTA --disk-limit-mib=200

The following command creates an individual user Quota Rule named NAME for
user with UID '100' using the required arguments:

    $ gcloud netapp volumes quota-rules create NAME \
      --location=us-central1 --volume=vol1 \
      --type=INDIVIDUAL_USER_QUOTA --target=100 --disk-limit-mib=200

The following command creates an individual group Quota Rule named NAME for
group with GID '1001' using the required arguments:

    $ gcloud netapp volumes quota-rules create NAME \
      --location=us-central1 --volume=vol1 \
      --type=INDIVIDUAL_GROUP_QUOTA --target=1001 --disk-limit-mib=200
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/quota-rules/create)

---
### `gcloud netapp volumes quota-rules delete`

Delete a Cloud NetApp Volume QuotaRule

Delete a Cloud NetApp Volume QuotaRule.

**Synopsis:**
```
gcloud netapp volumes quota-rules delete (QUOTA_RULE : --location=LOCATION)
    [--async] [--volume=VOLUME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Quota rule resource - The Quota Rule to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument quota_rule on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument quota_rule on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  QUOTA_RULE
     ID of the quota_rule or fully qualified identifier for the
     quota_rule.

     To set the quota_rule attribute:
     + provide the argument quota_rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the quota_rule.

     To set the location attribute:
     + provide the argument quota_rule on the command line with a fully
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
The following command deletes a QuotaRule named NAME using the required
arguments:

    $ gcloud netapp volumes quota-rules delete NAME \
      --location=us-central1 --volume=vol1

To delete a QuotaRule named NAME asynchronously, run the following command:

    $ gcloud netapp volumes quota-rules delete NAME \
      --location=us-central1 --volume=vol1 --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/quota-rules/delete)

---
### `gcloud netapp volumes quota-rules describe`

Describe a Cloud NetApp Volume Quota Rule

Describe a Cloud NetApp Volume Quota Rule.

**Synopsis:**
```
gcloud netapp volumes quota-rules describe
    (QUOTA_RULE : --location=LOCATION) [--volume=VOLUME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Quota rule resource - The Quota Rule to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument quota_rule on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument quota_rule on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  QUOTA_RULE
     ID of the quota_rule or fully qualified identifier for the
     quota_rule.

     To set the quota_rule attribute:
     + provide the argument quota_rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the quota_rule.

     To set the location attribute:
     + provide the argument quota_rule on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--volume` | VOLUME |  | _[* set the property netapp/location.]_ ID of the volume or fully qualified identifier for the volume. To set the volume attribute: + provide the argument --volume on the command line. |


**Examples:**
```bash
The following command describes a Quota Rule named NAME in the given
location and volume:

    $ gcloud netapp volumes quota-rules describe NAME \
      --location=us-central1 --volume=vol1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/quota-rules/describe)

---
### `gcloud netapp volumes quota-rules list`

List Cloud NetApp Volume QuotaRules

Lists Cloud NetApp Volume QuotaRules.

**Synopsis:**
```
gcloud netapp volumes quota-rules list [--location=LOCATION]
    [--volume=VOLUME] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + uses all locations by default.; + set the property netapp/location. |
| `--volume` | VOLUME |  | _[* set the property netapp/location.]_ ID of the volume or fully qualified identifier for the volume. To set the volume attribute: + provide the argument --volume on the command line. |


**Examples:**
```bash
The following command lists all QuotaRules in the given location and
volume:

    $ gcloud netapp volumes quota-rules list --location=us-central1 \
      --volume=vol1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/quota-rules/list)

---
### `gcloud netapp volumes quota-rules update`

Update a Cloud NetApp Volume QuotaRule

Update a Cloud NetApp Volume QuotaRule and its specified parameters.

**Synopsis:**
```
gcloud netapp volumes quota-rules update (QUOTA_RULE : --location=LOCATION)
    [--async] [--description=DESCRIPTION] [--disk-limit-mib=DISK_LIMIT_MIB]
    [--update-labels=[KEY=VALUE,...]] [--volume=VOLUME]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Quota rule resource - The Quota rule to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument quota_rule on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument quota_rule on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  QUOTA_RULE
     ID of the quota_rule or fully qualified identifier for the
     quota_rule.

     To set the quota_rule attribute:
     + provide the argument quota_rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the quota_rule.

     To set the location attribute:
     + provide the argument quota_rule on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Quota rule |
| `--disk-limit-mib` | DISK_LIMIT_MIB |  | The disk limit in MiB for the quota rule. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command updates a QuotaRule named NAME and its specified
parameters:

    $ gcloud netapp volumes quota-rules update NAME \
      --location=us-central1 --description="new" \
      --disk-limit-mib=100 --update-labels=key2=val2 --volume=vol1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/quota-rules/update)

---

## `gcloud netapp volumes replications` — create and manage Cloud NetApp Volume Replications
### `gcloud netapp volumes replications create`

Create a Cloud NetApp Volume Replication

Create a Cloud NetApp Volume Replication.

**Synopsis:**
```
gcloud netapp volumes replications create
    (REPLICATION : --location=LOCATION)
    --destination-volume-parameters=[description=DESCRIPTION],
      [share_name=SHARE_NAME],[storage_pool=STORAGE_POOL],
      [tiering_policy=TIERING_POLICY],[volume_id=VOLUME_ID]
    --replication-schedule=REPLICATION_SCHEDULE [--async]
    [--cluster-location=CLUSTER_LOCATION] [--description=DESCRIPTION]
    [--labels=[KEY=VALUE,...]] [--volume=VOLUME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Replication resource - The Replication to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  REPLICATION
     ID of the replication or fully qualified identifier for the
     replication.

     To set the replication attribute:
     + provide the argument replication on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the replication.

     To set the location attribute:
     + provide the argument replication on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-volume-parameters` | [description=DESCRIPTION],[share_name=SHARE_NAME],[storage_pool=STORAGE_POOL],[tiering_policy=TIERING_POLICY],[volume_id=VOLUME_ID] |  | Required, sets destination_volume_parameters value. description Sets description value. share_name Sets share_name value. storage_pool Required, sets storage_pool value. tiering_policy Sets tiering_policy value. cooling-threshold-days Sets cooling-threshold-days value. tier-action Sets tier-action value. volume_id Sets volume_id value. Shorthand Example: --destination-volume-parameters='description=string,share_name=string,storage_pool=string,tiering_policy={"cooling-threshold-days": int, "tier-action": "string"},volume_id=string' JSON Example: --destination-volume-parameters='{"description": "string", "share_name": "string", "storage_pool": "string", "tiering_policy": {"cooling-threshold-days": int, "tier-action": "string"}, "volume_id": "string"}' File Example: --destination-volume-parameters=path_to_file.(yaml\|json) |
| `--replication-schedule` | REPLICATION_SCHEDULE |  | The schedule for the Replication. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cluster-location` | CLUSTER_LOCATION |  | Location of the user cluster. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Replication |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command creates a Replication named NAME using the required
arguments:

    $ gcloud netapp volumes replications create NAME \
      --location=us-central1 --volume=vol1 \
      --replication-schedule=EVERY_10_MINUTES \
      --destination-volume-parameters=storage_pool=sp1,\
    volume_id=vol2,share_name=share2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/replications/create)

---
### `gcloud netapp volumes replications delete`

Delete a Cloud NetApp Volume Replication

Delete a Cloud NetApp Volume Replication.

**Synopsis:**
```
gcloud netapp volumes replications delete
    (REPLICATION : --location=LOCATION) [--async] [--volume=VOLUME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Replication resource - The Replication to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  REPLICATION
     ID of the replication or fully qualified identifier for the
     replication.

     To set the replication attribute:
     + provide the argument replication on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the replication.

     To set the location attribute:
     + provide the argument replication on the command line with a fully
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
The following command deletes a Replication named NAME using the required
arguments:

    $ gcloud netapp volumes replications delete NAME \
      --location=us-central1 --volume=vol1

To delete a Replication named NAME asynchronously, run the following
command:

    $ gcloud netapp volumes replications delete NAME \
      --location=us-central1 --volume=vol1 --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/replications/delete)

---
### `gcloud netapp volumes replications describe`

Describe a Cloud NetApp Volume Replication

Describe a Cloud NetApp Volume Replication.

**Synopsis:**
```
gcloud netapp volumes replications describe
    (REPLICATION : --location=LOCATION) [--volume=VOLUME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Replication resource - The Replication to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  REPLICATION
     ID of the replication or fully qualified identifier for the
     replication.

     To set the replication attribute:
     + provide the argument replication on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the replication.

     To set the location attribute:
     + provide the argument replication on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--volume` | VOLUME |  | _[* set the property netapp/location.]_ ID of the volume or fully qualified identifier for the volume. To set the volume attribute: + provide the argument --volume on the command line. |


**Examples:**
```bash
The following command describes a Replication named NAME in the given
location and volume:

    $ gcloud netapp volumes replications describe NAME \
      --location=us-central1 --volume=vol1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/replications/describe)

---
### `gcloud netapp volumes replications establish-peering`

Establish peering for Hybrid replication

Establish peering for Hybrid replication.

**Synopsis:**
```
gcloud netapp volumes replications establish-peering
    (REPLICATION : --location=LOCATION)
    --peer-cluster-name=PEER_CLUSTER_NAME --peer-svm-name=PEER_SVM_NAME
    --peer-volume-name=PEER_VOLUME_NAME [--async]
    [--peer-ip-addresses=PEER_IP_ADDRESS,[...]] [--volume=VOLUME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Replication resource - The Hybrid replication to establish peering for.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  REPLICATION
     ID of the replication or fully qualified identifier for the
     replication.

     To set the replication attribute:
     + provide the argument replication on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the replication.

     To set the location attribute:
     + provide the argument replication on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--peer-cluster-name` | PEER_CLUSTER_NAME |  | Name of the destination cluster to be peered with the source cluster. |
| `--peer-svm-name` | PEER_SVM_NAME |  | Name of the local source vserver svm to be peered with the destination cluster. |
| `--peer-volume-name` | PEER_VOLUME_NAME |  | Name of the source volume to be peered with the destination volume. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--peer-ip-addresses` | PEER_IP_ADDRESS,[...] |  | List of ip addresses to be used for peering. This is required for cluster peering, not required for svm peering. |


**Examples:**
```bash
The following command establishes peering for Hybrid replication named NAME
using the arguments specified:

    $ gcloud netapp volumes replications establish-peering NAME \
      --volume=volume1 --peer-cluster-name=peer-cluster-name1 \
      --peer-svm-name=peer-svm-name1 \
      --peer-volume-name=peer-volume-name1 \
      --peer-ip-addresses=1.1.1.1,2.2.2.2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/replications/establish-peering)

---
### `gcloud netapp volumes replications list`

List Cloud NetApp Volume Replications

Lists Cloud NetApp Volume Replications.

**Synopsis:**
```
gcloud netapp volumes replications list [--location=LOCATION]
    [--volume=VOLUME] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + uses all locations by default.; + set the property netapp/location. |
| `--volume` | VOLUME |  | _[* set the property netapp/location.]_ ID of the volume or fully qualified identifier for the volume. To set the volume attribute: + provide the argument --volume on the command line. |


**Examples:**
```bash
The following command lists all Replications in the given location and
volume:

    $ gcloud netapp volumes replications list --location=us-central1 \
      --volume=vol1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/replications/list)

---
### `gcloud netapp volumes replications resume`

Resume a Cloud NetApp Volume Replication

Resume a Cloud NetApp Volume Replication.

**Synopsis:**
```
gcloud netapp volumes replications resume
    (REPLICATION : --location=LOCATION) [--async] [--volume=VOLUME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Replication resource - The Replication to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  REPLICATION
     ID of the replication or fully qualified identifier for the
     replication.

     To set the replication attribute:
     + provide the argument replication on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the replication.

     To set the location attribute:
     + provide the argument replication on the command line with a fully
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
The following command resumes a Replication named NAME using the required
arguments:

    $ gcloud netapp volumes replications resume NAME \
      --location=us-central1 --volume=vol1

To resume a Replication named NAME asynchronously, run the following
command:

    $ gcloud netapp volumes replications resume NAME \
      --location=us-central1 --volume=vol1 --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/replications/resume)

---
### `gcloud netapp volumes replications reverse`

Reverse a Cloud NetApp Volume Replication's direction

Reverse a Cloud NetApp Volume Replication.

**Synopsis:**
```
gcloud netapp volumes replications reverse
    (REPLICATION : --location=LOCATION) [--async] [--volume=VOLUME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Replication resource - The Replication to reverse direction. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  REPLICATION
     ID of the replication or fully qualified identifier for the
     replication.

     To set the replication attribute:
     + provide the argument replication on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the replication.

     To set the location attribute:
     + provide the argument replication on the command line with a fully
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
The following command reverses a Replication named NAME using the required
arguments:

    $ gcloud netapp volumes replications reverse NAME \
      --location=us-central1 --volume=vol1

To reverse a Replication named NAME asynchronously, run the following
command:

    $ gcloud netapp volumes replications reverse NAME \
      --location=us-central1 --volume=vol1 --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/replications/reverse)

---
### `gcloud netapp volumes replications stop`

Stop a Cloud NetApp Volume Replication

Stop a Cloud NetApp Volume Replication.

**Synopsis:**
```
gcloud netapp volumes replications stop (REPLICATION : --location=LOCATION)
    [--async] [--force] [--volume=VOLUME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Replication resource - The Replication to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  REPLICATION
     ID of the replication or fully qualified identifier for the
     replication.

     To set the replication attribute:
     + provide the argument replication on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the replication.

     To set the location attribute:
     + provide the argument replication on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | Indicates whether to stop replication forcefully while data transfer is in progress. Warning! if force is true, this will abort any current transfers and can lead to data loss due to partial transfer. If force is false, stop replication will fail while data transfer is in progress and you will need to retry later. |


**Examples:**
```bash
The following command stops a Replication named NAME using the required
arguments:

    $ gcloud netapp volumes replications stop NAME \
      --location=us-central1 --volume=vol1

To stop a Replication named NAME asynchronously, run the following command:

    $ gcloud netapp volumes replications stop NAME \
      --location=us-central1 --volume=vol1 --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/replications/stop)

---
### `gcloud netapp volumes replications sync`

Sync a Cloud NetApp Volume Replication

Sync a Cloud NetApp Volume Replication.

**Synopsis:**
```
gcloud netapp volumes replications sync (REPLICATION : --location=LOCATION)
    [--async] [--volume=VOLUME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Replication resource - The Replication to sync. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  REPLICATION
     ID of the replication or fully qualified identifier for the
     replication.

     To set the replication attribute:
     + provide the argument replication on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the replication.

     To set the location attribute:
     + provide the argument replication on the command line with a fully
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
The following command syncs a Replication named NAME using the required
arguments:

    $ gcloud netapp volumes replications sync NAME \
      --location=us-central1 --volume=vol1

To sync a Replication named NAME asynchronously, run the following command:

    $ gcloud netapp volumes replications sync NAME \
      --location=us-central1 --volume=vol1 --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/replications/sync)

---
### `gcloud netapp volumes replications update`

Update a Cloud NetApp Volume Replication

Update a Cloud NetApp Volume Replication and its specified parameters.

**Synopsis:**
```
gcloud netapp volumes replications update
    (REPLICATION : --location=LOCATION) [--async]
    [--cluster-location=CLUSTER_LOCATION] [--description=DESCRIPTION]
    [--replication-schedule=REPLICATION_SCHEDULE]
    [--update-labels=[KEY=VALUE,...]] [--volume=VOLUME]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Replication resource - The Replication to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument replication on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  REPLICATION
     ID of the replication or fully qualified identifier for the
     replication.

     To set the replication attribute:
     + provide the argument replication on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the replication.

     To set the location attribute:
     + provide the argument replication on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cluster-location` | CLUSTER_LOCATION |  | Location of the user cluster. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Replication |
| `--replication-schedule` | REPLICATION_SCHEDULE |  | The schedule for the Replication. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command updates a Replication named NAME and its specified
parameters:

    $ gcloud netapp volumes replications update NAME \
      --location=us-central1 --volume=vol1 \
      --replication-schedule=EVERY_5_MINUTES \
      --description="new description" --cluster-location= us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/replications/update)

---

## `gcloud netapp volumes snapshots` — create and manage Cloud NetApp Volume Snapshots
### `gcloud netapp volumes snapshots create`

Create a Cloud NetApp Volume Snapshot

Create a Cloud NetApp Volume Snapshot.

**Synopsis:**
```
gcloud netapp volumes snapshots create (SNAPSHOT : --location=LOCATION)
    [--async] [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--volume=VOLUME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Snapshot resource - The Snapshot to create. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument snapshot on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument snapshot on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  SNAPSHOT
     ID of the snapshot or fully qualified identifier for the snapshot.

     To set the snapshot attribute:
     + provide the argument snapshot on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the snapshot.

     To set the location attribute:
     + provide the argument snapshot on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Snapshot |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command creates a Snapshot named NAME using the required
arguments:

    $ gcloud netapp volumes snapshots create NAME \
      --location=us-central1 --volume=vol1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/snapshots/create)

---
### `gcloud netapp volumes snapshots delete`

Delete a Cloud NetApp Volume Snapshot

Delete a Cloud NetApp Volume Snapshot.

**Synopsis:**
```
gcloud netapp volumes snapshots delete (SNAPSHOT : --location=LOCATION)
    [--async] [--volume=VOLUME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Snapshot resource - The Snapshot to delete. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument snapshot on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument snapshot on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  SNAPSHOT
     ID of the snapshot or fully qualified identifier for the snapshot.

     To set the snapshot attribute:
     + provide the argument snapshot on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the snapshot.

     To set the location attribute:
     + provide the argument snapshot on the command line with a fully
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
The following command deletes a Snapshot named NAME in the given location
and volume:

    $ gcloud netapp volumes snapshots delete NAME \
      --location=us-central1 --volume=vol1

To delete a Snapshot named NAME asynchronously, run the following command:

    $ gcloud netapp volumes snapshots delete NAME \
      --location=us-central1 --volume=vol1 --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/snapshots/delete)

---
### `gcloud netapp volumes snapshots describe`

Describe a Cloud NetApp Volume Snapshot

Describe a Cloud NetApp Volume Snapshot.

**Synopsis:**
```
gcloud netapp volumes snapshots describe (SNAPSHOT : --location=LOCATION)
    [--volume=VOLUME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Snapshot resource - The Snapshot to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument snapshot on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument snapshot on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  SNAPSHOT
     ID of the snapshot or fully qualified identifier for the snapshot.

     To set the snapshot attribute:
     + provide the argument snapshot on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the snapshot.

     To set the location attribute:
     + provide the argument snapshot on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--volume` | VOLUME |  | _[* set the property netapp/location.]_ ID of the volume or fully qualified identifier for the volume. To set the volume attribute: + provide the argument --volume on the command line. |


**Examples:**
```bash
The following command describes a Snapshot named NAME in the given location
and volume:

    $ gcloud netapp volumes snapshots describe NAME \
      --location=us-central1 --volume=vol1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/snapshots/describe)

---
### `gcloud netapp volumes snapshots list`

List Cloud NetApp Volume Snapshots

Lists Cloud NetApp Volume Snapshots.

**Synopsis:**
```
gcloud netapp volumes snapshots list [--location=LOCATION]
    [--volume=VOLUME] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + uses all locations by default.; + set the property netapp/location. |
| `--volume` | VOLUME |  | _[* set the property netapp/location.]_ ID of the volume or fully qualified identifier for the volume. To set the volume attribute: + provide the argument --volume on the command line. |


**Examples:**
```bash
The following command lists all Snapshots in the given location and volume:

    $ gcloud netapp volumes snapshots list --location=us-central1 \
      --volume=vol1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/snapshots/list)

---
### `gcloud netapp volumes snapshots update`

Update a Cloud NetApp Volume Snapshot

Update a Cloud NetApp Volume Snapshot and its specified parameters.

**Synopsis:**
```
gcloud netapp volumes snapshots update (SNAPSHOT : --location=LOCATION)
    [--async] [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--volume=VOLUME] [--clear-labels | --remove-labels=[KEY,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Snapshot resource - The Snapshot to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument snapshot on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the volume attribute:
 * provide the argument snapshot on the command line with a fully
   specified name;
 * provide the argument --volume on the command line.

This must be specified.

  SNAPSHOT
     ID of the snapshot or fully qualified identifier for the snapshot.

     To set the snapshot attribute:
     + provide the argument snapshot on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the snapshot.

     To set the location attribute:
     + provide the argument snapshot on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Snapshot |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command updates a Snapshot named NAME and its specified
parameters:

    $ gcloud netapp volumes snapshots update NAME \
      --location=us-central1 --description="new" \
      --update-labels=key2=val2 --volume=vol1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/volumes/snapshots/update)

---