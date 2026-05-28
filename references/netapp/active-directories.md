# gcloud netapp active-directories

create and manage Cloud NetApp Active Directories

### `gcloud netapp active-directories create`

Create a Cloud NetApp Active Directory

Creates an AD (Active Directory) config for Cloud NetApp Volumes.

**Synopsis:**
```
gcloud netapp active-directories create
    (ACTIVE_DIRECTORY : --location=LOCATION) --dns=DNS --domain=DOMAIN
    --net-bios-prefix=NET_BIOS_PREFIX --password=PASSWORD
    --username=USERNAME [--administrators=[ADMINISTRATOR,...]] [--async]
    [--backup-operators=[BACKUP_OPERATOR,...]] [--description=DESCRIPTION]
    [--enable-aes=ENABLE_AES] [--enable-ldap-signing=ENABLE_LDAP_SIGNING]
    [--encrypt-dc-connections=ENCRYPT_DC_CONNECTIONS]
    [--kdc-hostname=KDC_HOSTNAME] [--kdc-ip=KDC_IP]
    [--labels=[KEY=VALUE,...]] [--nfs-users-with-ldap=NFS_USERS_WITH_LDAP]
    [--organizational-unit=ORGANIZATIONAL_UNIT]
    [--security-operators=[SECURITY_OPERATOR,...]] [--site=SITE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Active directory resource - The Active Directory to create. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument active_directory on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ACTIVE_DIRECTORY
     ID of the active_directory or fully qualified identifier for the
     active_directory.

     To set the active_directory attribute:
     + provide the argument active_directory on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the active_directory.

     To set the location attribute:
     + provide the argument active_directory on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dns` | DNS |  | A comma separated list of DNS server IP addresses for the Active Directory domain. |
| `--domain` | DOMAIN |  | The Active Directory domain. |
| `--net-bios-prefix` | NET_BIOS_PREFIX |  | NetBIOS prefix name of the server. |
| `--password` | PASSWORD |  | Password of the Active Directory domain administrator. |
| `--username` | USERNAME |  | Username of the Active Directory domain administrator. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--administrators` | [ADMINISTRATOR,...] |  | Members of the Active Directory built-in Administrators group. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--backup-operators` | [BACKUP_OPERATOR,...] |  | Users to be added to the Built-in Backup Operator Active Directory group. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Active Directory |
| `--enable-aes` | ENABLE_AES |  | The Boolean value indiciating whether AES encryption will be enabled for SMB communication. |
| `--enable-ldap-signing` | ENABLE_LDAP_SIGNING |  | Boolean flag that specifies whether or not LDAP traffic needs to be signed. |
| `--encrypt-dc-connections` | ENCRYPT_DC_CONNECTIONS |  | Boolean flag that specifies whether traffic between SMB server to Domain Controller (DC) will be encrypted. |
| `--kdc-hostname` | KDC_HOSTNAME |  | Name of the Active Directory machine. |
| `--kdc-ip` | KDC_IP |  | KDC server IP address for the Active Directory machine. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--nfs-users-with-ldap` | NFS_USERS_WITH_LDAP |  | Boolean flag that allows access to local users and LDAP users. If access is needed only for LDAP users, it has to be disabled. |
| `--organizational-unit` | ORGANIZATIONAL_UNIT |  | The Organizational Unit (OU) within the Windows Active Directory the user belongs to. |
| `--security-operators` | [SECURITY_OPERATOR,...] |  | Domain users to be given the Security privilege. |
| `--site` | SITE |  | The Active Directory site the service will limit Domain Controller discovery to. |


**Examples:**
```bash
The following command creates an AD named AD_NAME with the required
arguments:

    $ gcloud netapp active-directories create AD_NAME \
      --location=us-central1 --domain=example-domain.com \
      --dns=0.0.0.0 --net-bios-prefix=prefix-1 --enable-aes=true \
      --username=user1 --password="secure1" \
      --backup-operators=backup_op1,backup_op2 \
      --security-operators=sec_op1,sec_op2 --enable-ldap-signing=false
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/active-directories/create)

---
### `gcloud netapp active-directories delete`

Delete a Cloud NetApp Active Directory

Deletes an AD (Active Directory) config for Cloud NetApp Volumes.

**Synopsis:**
```
gcloud netapp active-directories delete
    (ACTIVE_DIRECTORY : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Active directory resource - The Active Directory to delete. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument active_directory on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ACTIVE_DIRECTORY
     ID of the active_directory or fully qualified identifier for the
     active_directory.

     To set the active_directory attribute:
     + provide the argument active_directory on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the active_directory.

     To set the location attribute:
     + provide the argument active_directory on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes an AD named AD_NAME with the required
arguments:

    $ gcloud netapp active-directories delete AD_NAME \
      --location=us-central1

To delete a AD Config asynchronously, run the following command:

    $ gcloud netapp active-directories delete AD_NAME \
      --location=us-central1 --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/active-directories/delete)

---
### `gcloud netapp active-directories describe`

Show metadata for a Cloud NetApp Active Directory

Describes an AD (Active Directory) config for Cloud NetApp Volumes.

**Synopsis:**
```
gcloud netapp active-directories describe
    (ACTIVE_DIRECTORY : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Active directory resource - The Active Directory to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument active_directory on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ACTIVE_DIRECTORY
     ID of the active_directory or fully qualified identifier for the
     active_directory.

     To set the active_directory attribute:
     + provide the argument active_directory on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the active_directory.

     To set the location attribute:
     + provide the argument active_directory on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Examples:**
```bash
The following command describes an AD named AD_NAME with the required
arguments:

    $ gcloud netapp active-directories describe AD_NAME \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/active-directories/describe)

---
### `gcloud netapp active-directories list`

List Cloud NetApp Active Directories

Lists AD (Active Directory) configs for Cloud NetApp Volumes.

**Synopsis:**
```
gcloud netapp active-directories list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + uses all locations by default.; + set the property netapp/location. |


**Examples:**
```bash
The following command lists AD configs in the given project and location:

    $ gcloud netapp active-directories list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/active-directories/list)

---
### `gcloud netapp active-directories update`

Update a Cloud NetApp Active Directory

Updates AD (Active Directory) configs for Cloud NetApp Volumes.

**Synopsis:**
```
gcloud netapp active-directories update
    (ACTIVE_DIRECTORY : --location=LOCATION) --dns=DNS --domain=DOMAIN
    --net-bios-prefix=NET_BIOS_PREFIX --password=PASSWORD
    --username=USERNAME [--administrators=[ADMINISTRATOR,...]] [--async]
    [--backup-operators=[BACKUP_OPERATOR,...]] [--description=DESCRIPTION]
    [--enable-aes=ENABLE_AES] [--enable-ldap-signing=ENABLE_LDAP_SIGNING]
    [--encrypt-dc-connections=ENCRYPT_DC_CONNECTIONS]
    [--kdc-hostname=KDC_HOSTNAME] [--kdc-ip=KDC_IP]
    [--nfs-users-with-ldap=NFS_USERS_WITH_LDAP]
    [--organizational-unit=ORGANIZATIONAL_UNIT]
    [--security-operators=[SECURITY_OPERATOR,...]] [--site=SITE]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Active directory resource - The Active Directory to update. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument active_directory on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ACTIVE_DIRECTORY
     ID of the active_directory or fully qualified identifier for the
     active_directory.

     To set the active_directory attribute:
     + provide the argument active_directory on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the active_directory.

     To set the location attribute:
     + provide the argument active_directory on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dns` | DNS |  | A comma separated list of DNS server IP addresses for the Active Directory domain. |
| `--domain` | DOMAIN |  | The Active Directory domain. |
| `--net-bios-prefix` | NET_BIOS_PREFIX |  | NetBIOS prefix name of the server. |
| `--password` | PASSWORD |  | Password of the Active Directory domain administrator. |
| `--username` | USERNAME |  | Username of the Active Directory domain administrator. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--administrators` | [ADMINISTRATOR,...] |  | Members of the Active Directory built-in Administrators group. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--backup-operators` | [BACKUP_OPERATOR,...] |  | Users to be added to the Built-in Backup Operator Active Directory group. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Active Directory |
| `--enable-aes` | ENABLE_AES |  | The Boolean value indiciating whether AES encryption will be enabled for SMB communication. |
| `--enable-ldap-signing` | ENABLE_LDAP_SIGNING |  | Boolean flag that specifies whether or not LDAP traffic needs to be signed. |
| `--encrypt-dc-connections` | ENCRYPT_DC_CONNECTIONS |  | Boolean flag that specifies whether traffic between SMB server to Domain Controller (DC) will be encrypted. |
| `--kdc-hostname` | KDC_HOSTNAME |  | Name of the Active Directory machine. |
| `--kdc-ip` | KDC_IP |  | KDC server IP address for the Active Directory machine. |
| `--nfs-users-with-ldap` | NFS_USERS_WITH_LDAP |  | Boolean flag that allows access to local users and LDAP users. If access is needed only for LDAP users, it has to be disabled. |
| `--organizational-unit` | ORGANIZATIONAL_UNIT |  | The Organizational Unit (OU) within the Windows Active Directory the user belongs to. |
| `--security-operators` | [SECURITY_OPERATOR,...] |  | Domain users to be given the Security privilege. |
| `--site` | SITE |  | The Active Directory site the service will limit Domain Controller discovery to. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command updates an AD config in the given project and
location with specified arguments:

    $ gcloud netapp active-directories update AD_NAME \
      --location=us-central1 --domain=new-domain.com --dns=1.1.1.1 \
      --site=new_site --net-bios-prefix=new_prefix \
      --organizational-unit=ou2 --enable-aes=true --username=user2 \
      --password="secure2" --backup-operators=backup_op1,backup_op2 \
      --security-operators=secure_op1,secure_op2 \
      --administrators=admin_op1,admin_op2 \
      --enable-ldap-signing=true --encrypt-dc-connections=yes \
      --kdc-hostname=kdc-host1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/active-directories/update)

---