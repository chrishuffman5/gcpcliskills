# gcloud active-directory domains

manage Managed Microsoft AD domains

### `gcloud active-directory domains create`

Create a Managed Microsoft AD domain

Create a new Managed Microsoft AD domain with the given name using Google
Cloud's Managed Service for Microsoft Active Directory.

This command can fail for the following reasons:
  o An AD domain with the same name already exists.
  o The active account does not have permission to create AD domains.
  o There is an overlap between the provided CIDR range and authorized
    network's CIDR.
  o A valid region was not provided.

**Synopsis:**
```
gcloud active-directory domains create DOMAIN --region=[REGION,...]
    --reserved-ip-range=RESERVED_IP_RANGE [--admin-name=ADMIN_NAME]
    [--async] [--authorized-networks=[AUTHORIZED_NETWORKS,...]]
    [--enable-audit-logs] [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the managed Managed Microsoft AD domain you want
to create. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | [REGION,...] |  | Google Compute Engine region in which to provision domain controllers. |
| `--reserved-ip-range` | RESERVED_IP_RANGE |  | Classless Inter-Domain Routing range of internal addresses that are reserved for this domain. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-name` | ADMIN_NAME |  | Name of the administrator that may be used to perform Active Directory operations. This is a delegated administrator account provisioned by our service. If left unspecified MIAdmin will be used. This is different from both the domain administrator and the Directory Services Restore Mode (DSRM) administrator. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--authorized-networks` | [AUTHORIZED_NETWORKS,...] |  | Names of the Google Compute Engine networks to which the domain will be connected. |
| `--enable-audit-logs` |  |  | If specified, Active Directory data audit logs are enabled for the domain. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. |


**Examples:**
```bash
The following command creates an AD domain with the name my-domain.com in
region us-central1, a network peering to my-network and consuming the IP
address range 10.172.0.0/24.

    $ gcloud active-directory domains create my-domain.com \
        --region=us-central1 --reserved-ip-range="10.172.0.0/24" \
        --authorized-networks=projects/my-project/global/networks/\
    my-network
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/create)

---
### `gcloud active-directory domains delete`

Delete a managed Microsoft Active Directory domain

Delete a managed Microsoft Active Directory (AD) domain with the given
fully-qualified domain name.

This command can fail for the following reasons:
  o The AD domain specified does not exist.
  o The active account does not have permission to access the given AD
    domain.

**Synopsis:**
```
gcloud active-directory domains delete DOMAIN [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the managed Managed Microsoft AD domain you want
to delete. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes an AD domain with the name my-domain.com.

    $ gcloud active-directory domains delete my-domain.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/delete)

---
### `gcloud active-directory domains describe`

Describe a Managed Microsoft AD domain

Show metadata for a Managed Microsoft AD domain.

Displays all metadata associated with a Active Directory domain given a
valid AD domain fully-qualified domain name.

This command can fail for the following reasons:
  o The domain specified does not exist.
  o The active account does not have permission to access the given
    domain.

**Synopsis:**
```
gcloud active-directory domains describe DOMAIN [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the Managed Microsoft AD domain you want to
describe. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.
```

**Examples:**
```bash
The following command prints metadata for an AD domain with the name
my-domain.com.

    $ gcloud active-directory domains describe my-domain.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/describe)

---
### `gcloud active-directory domains describe-ldaps-settings`

Describe the LDAPS settings of a Managed Microsoft AD domain

Describe the Lightweight Directory Access Protocol over TLS/SSL (LDAPS)
settings of a Managed Microsoft AD domain.

This command can fail for the following reasons:
  o The domain specified does not exist.
  o The active account does not have permission to view LDAPS settings
    for the domain.

**Synopsis:**
```
gcloud active-directory domains describe-ldaps-settings DOMAIN
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the Managed Microsoft AD domain you want to
describe. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.
```

**Examples:**
```bash
The following command shows the LDAPS settings for an AD domain with the
name my-domain.com.

    $ gcloud active-directory domains describe-ldaps-settings \
        my-domain.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/describe-ldaps-settings)

---
### `gcloud active-directory domains extend-schema`

Initiate schema extension for a Managed Microsoft AD domain

Initiate schema extension for a Managed Microsoft AD domain.

This command can fail for the following reasons:
  o The specified domain doesn't exist.
  o The specified domain is either being created or updated.
  o The specified domain is under maintenance.
  o The active account doesn't have permission to initiate schema
    extension on the specified domain.

**Synopsis:**
```
gcloud active-directory domains extend-schema DOMAIN
    --description=DESCRIPTION --ldif-file=PATH_TO_FILE [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the Managed Microsoft AD domain for which you
want to extend schema. This represents a Cloud resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of schema change. |
| `--ldif-file` | PATH_TO_FILE |  | Local LDIF file path that contains commands for schema extension. The file size can't be larger than 1 MB. Use a full or relative path to a local file containing the value of ldif_file. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command initiates a schema extension for the domain
my-domain.com in project my-project, with description Test Description,
using the LDIF file demo.ldif

    $ gcloud active-directory domains extend-schema my-domain.com \
        --description="Test Description" --ldif-file=demo.ldf \
        --project=my-project --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/extend-schema)

---
### `gcloud active-directory domains get-iam-policy`

Describe the IAM policy for a Managed Microsoft AD domain

gcloud active-directory domains get-iam-policy displays the IAM policy
associated with an Managed Microsoft AD domain. If formatted as JSON, the
output can be edited and used as a policy file for set-iam-policy. The
output includes an "etag" field identifying the version emitted and
allowing detection of concurrent policy updates.

This command can fail for the following reasons:
  o The domain specified does not exist.
  o The active account does not have permission to access the given
    domain's IAM policies.

**Synopsis:**
```
gcloud active-directory domains get-iam-policy DOMAIN [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the Managed Microsoft AD domain that you want to
get the IAM policy for. This represents a Cloud resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.
```

**Examples:**
```bash
To print the IAM policy for my-domain.com, run:

    $ gcloud active-directory domains get-iam-policy my-domain.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/get-iam-policy)

---
### `gcloud active-directory domains list`

List Managed Microsoft AD domains

List all Managed Microsoft AD domains in the specified project.

You can specify the maximum number of domains to list using the --limit
flag.

**Synopsis:**
```
gcloud active-directory domains list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists a maximum of five domains:

    $ gcloud active-directory domains list --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/list)

---
### `gcloud active-directory domains reset-admin-password`

Reset the admin password for a Managed Microsoft AD domain

Reset the delegated admin password for a Managed Microsoft AD domain given
a valid AD domain fully-qualified domain name.

This command can fail for the following reasons:
  o The AD domain specified does not exist.
  o The active account does not have permission to access the given AD
    domain.

**Synopsis:**
```
gcloud active-directory domains reset-admin-password DOMAIN
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the Managed Microsoft AD domain you want to
reset the password for. This represents a Cloud resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.
```

**Examples:**
```bash
The following command resets the admin password for an AD domain with the
name my-domain.com.

    $ gcloud active-directory domains reset-admin-password my-domain.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/reset-admin-password)

---
### `gcloud active-directory domains restore`

Restore a domain from the specified backup

Restore a Managed Microsoft AD domain to a previous point in time when the
backup was taken.

This command can fail for the following reasons:
  o The specified domain doesn't exist.
  o The specified backup doesn't exist.
  o The active account doesn't have permission to restore the specified
    domain.

**Synopsis:**
```
gcloud active-directory domains restore DOMAIN --backup=BACKUP [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the Managed Microsoft AD domain you want to
restore. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup` | BACKUP |  | Name of the domain backup from which you want to restore the Managed Microsoft AD domain. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To restore the domain my-domain.com from backup my-backup, run:

    $ gcloud active-directory domains restore my-domain.com \
        --backup=my-backup --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/restore)

---
### `gcloud active-directory domains set-iam-policy`

Set the IAM policy for a Managed Microsoft AD domain

Set the IAM policy associated with a Managed Microsoft AD domain.

This command can fail for the following reasons:
  o The domain specified does not exist.
  o The active account does not have permission to access the given
    domain's IAM policies.

**Synopsis:**
```
gcloud active-directory domains set-iam-policy DOMAIN POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the Managed Microsoft AD domain you want to set
the IAM policy for. This represents a Cloud resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
To set the IAM policy for my-domain.com, run:

    $ gcloud active-directory domains set-iam-policy my-domain.com \
        policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/set-iam-policy)

---
### `gcloud active-directory domains update`

Update a Managed Microsoft AD domain

Update the metadata and/or configuration parameters of a managed Microsoft
AD domain.

This command can fail for the following reasons:
  o The AD domain specified does not exist.
  o The active account does not have permission to update the given AD
    domain.

**Synopsis:**
```
gcloud active-directory domains update DOMAIN [--async]
    [--enable-audit-logs] [--update-labels=[KEY=VALUE,...]]
    [--add-authorized-networks=[AUTH_NET1, AUTH_NET2, ...,...]
      | --remove-authorized-networks=[AUTH_NET1, AUTH_NET2, ...,...]]
    [--add-region=ADD_REGION | --remove-region=REMOVE_REGION]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the Managed Microsoft AD domain you want to
update. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--enable-audit-logs` |  |  | If specified, Active Directory data audit logs are enabled for the domain. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command updates an AD domain with the name my-domain.com to
add the two labels, env and service and to add a provisioned region
us-west1:

    $ gcloud active-directory domains update my-domain.com \
        --update-labels=env=test,service=foo --add-region=us-west1

This peers the domain my-domain.com to the network my-network.

    $ gcloud active-directory domains update my-domain.com \
        --add-authorized-networks=projects/my-project/global/networks/\
    my-network
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/update)

---
### `gcloud active-directory domains update-ldaps-settings`

Update the LDAPS settings for a domain

Update a Managed Microsoft AD domain's Lightweight Directory Access
Protocol over TLS/SSL (LDAPS) settings. You must be safelisted for the
Managed AD LDAPS Alpha in order to use this feature. Consult the API
documentation for a list of certificate requirements.

This command can fail for the following reasons:
  o The certificate is invalid.
  o The domain specified does not exist.
  o The active account does not have permission to view LDAPS settings
    for the domain.

**Synopsis:**
```
gcloud active-directory domains update-ldaps-settings DOMAIN
    (--clear-certificates | [--certificate-pfx-file=PATH_TO_FILE
      : --certificate-password=CERTIFICATE_PASSWORD]) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the managed Managed Microsoft AD domain you want
to update. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--clear-certificates` |  |  | _[Exactly one of these must be specified:]_ Disable LDAPS by deleting all existing certificates. Certificates will need to be re-uploaded if LDAPS is to be re-enabled. |
| `--certificate-pfx-file` | PATH_TO_FILE |  | _[Exactly one of these must be specified:]_ PKCS#12-formatted pfx file that specifies the certificate chain used to configure LDAPS. If certificate-password is not specified, command will prompt user for secret. Use a full or relative path to a local file containing the value of certificate_pfx_file. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--certificate-password` | CERTIFICATE_PASSWORD |  | _[Exactly one of these must be specified:]_ Password used to encrypt the PKCS#12 certificate. If not specified, command will prompt user for secret. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To enable LDAPS for the first time or update the certificates being used:

    $ gcloud active-directory domains update-ldaps-settings \
        my-domain.com \
        --certificate-pfx-file=certificate-chain-with-private-key.pfx \
        --certificate-password="password"

To disable LDAPS:

    $ gcloud active-directory domains update-ldaps-settings \
        my-domain.com --clear-certificates
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/update-ldaps-settings)

---

## `gcloud active-directory domains backups` — managed Microsoft AD Backups
### `gcloud active-directory domains backups create`

Create a Managed Microsoft AD domain backup

Create a new Managed Microsoft AD domain backup with the specified name
using Google Cloud's Managed Service for Microsoft Active Directory.

This command can fail for the following reasons:
  o The specified domain doesn't exist.
  o The specified domain is being created.
  o A backup already exists with the same target domain name.
  o The active account doesn't have permission to access the specified
    domain.
  o The active account doesn't have permission to create AD domain
    backups.

**Synopsis:**
```
gcloud active-directory domains backups create (BACKUP : --domain=DOMAIN)
    [--async] [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Name of the Managed Microsoft AD domain backup you want
to create. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --domain=DOMAIN
     The fully-qualified domain name of the Microsoft Active Directory
     domain.

     To set the domain attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --domain on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. |


**Examples:**
```bash
To create an AD domain backup named my-backup under domain my-domain.com,
run:

    $ gcloud active-directory domains backups create my-backup \
        --domain=my-domain.com --project=my-proj --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/backups/create)

---
### `gcloud active-directory domains backups delete`

Delete a Managed Microsoft AD domain backup

Delete a Managed Microsoft AD domain backup with the specified name using
Google Cloud's Managed Service for Microsoft Active Directory.

This command can fail for the following reasons:
  o The specified backup doesn't exist.
  o The active account doesn't have permission to access the specified
    domain.
  o The active account doesn't have permission to access the specified AD
    domain backup.

**Synopsis:**
```
gcloud active-directory domains backups delete (BACKUP : --domain=DOMAIN)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Name of the Managed Microsoft AD domain backup you want
to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --domain=DOMAIN
     The fully-qualified domain name of the Microsoft Active Directory
     domain.

     To set the domain attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --domain on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an AD domain backup my-backup under domain        `projects/my-proj/locations/global/domains/my-domain.com`, run:

    $ gcloud active-directory domains backups delete \
        projects/my-proj/locations/global/domains/my-domain.com/\
    backups/my-backup --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/backups/delete)

---
### `gcloud active-directory domains backups describe`

Describe a Managed Microsoft AD domain backup

Show metadata for a Managed Microsoft AD domain backup.

Displays all metadata associated with an Active Directory domain backup
when provided with a valid domain backup name.

This command can fail for the following reasons:
  o The specified domain backup doesn't exist.
  o The active account doesn't have permission to access the specified
    domain.

**Synopsis:**
```
gcloud active-directory domains backups describe (BACKUP : --domain=DOMAIN)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Name of the Managed Microsoft AD domain backup you want
to describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --domain=DOMAIN
     The fully-qualified domain name of the Microsoft Active Directory
     domain.

     To set the domain attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --domain on the command line.
```

**Examples:**
```bash
To display all metadata associated with an AD domain backup with the name
my-backup under the domain my-domain in project my-project, run:

    $ gcloud active-directory domains backups describe \
        projects/my-proj/locations/global/domains/my-domain.com/\
    backups/my-backup
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/backups/describe)

---
### `gcloud active-directory domains backups list`

List all Managed Microsoft AD domain backups

List all Managed Microsoft AD domain backups in the specified Managed
Microsoft AD domain.

Displays associated Active Directory domain backups.

This command can fail for the following reasons:
  o The active account doesn't have permission to access the specified
    domain.

**Synopsis:**
```
gcloud active-directory domains backups list --domain=DOMAIN
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--domain` | DOMAIN |  | _[This must be specified.]_ ID of the domain or fully qualified identifier for the domain. To set the domain attribute: + provide the argument --domain on the command line. |


**Examples:**
```bash
To list all AD domain backups in the project my-project under domain
my-domain.com, run:

    $ gcloud active-directory domains backups list \
        --project=my-project --domain=my-domain.com --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/backups/list)

---
### `gcloud active-directory domains backups update`

Update a Managed Microsoft AD domain backup

Update a Managed Microsoft AD domain backup.
  o The specified backup doesn't exist.
  o The active account doesn't have permission to access the specified
    domain.
  o The active account doesn't have permission to access the specified
    domain backup.

**Synopsis:**
```
gcloud active-directory domains backups update (BACKUP : --domain=DOMAIN)
    [--async] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Name of the Managed Microsoft AD domain backup you want
to update. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --domain=DOMAIN
     The fully-qualified domain name of the Microsoft Active Directory
     domain.

     To set the domain attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --domain on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update an AD domain backup my-backup under domain        `projects/my-proj/locations/global/domains/my-domain.com` with the labels `l1` and `l2`, run:

    $ gcloud active-directory domains backups update \
        projects/my-proj/locations/global/domains/my-domain.com/\
    backups/my-backup --update-labels=l1=1,l2=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/backups/update)

---

## `gcloud active-directory domains trusts` — manage Managed Microsoft AD domains
### `gcloud active-directory domains trusts create`

Create a Microsoft Active Directory Trust between a Managed Microsoft AD domain and another domain

Create a Microsoft Active Directory Trust between a Managed Microsoft AD
domain and another domain.

This command can fail for the following reasons:
  o The domain specified does not exist.
  o The active account does not have permission to access the given
    domain.
  o A trust already exists with the same target domain name.
  o The active account does not have permission to create AD trusts.

**Synopsis:**
```
gcloud active-directory domains trusts create DOMAIN
    --target-dns-ip-addresses=[TARGET_DNS_IP_ADDRESSES,...]
    --target-domain-name=TARGET_DOMAIN_NAME [--async]
    [--direction=DIRECTION; default="BIDIRECTIONAL"]
    [--handshake-secret=HANDSHAKE_SECRET] [--selective-authentication]
    [--type=TYPE; default="FOREST"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the Managed Microsoft AD domain you want to
create an AD trust from. This represents a Cloud resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-dns-ip-addresses` | [TARGET_DNS_IP_ADDRESSES,...] |  | Target DNS server IP addresses that can resolve the target domain. Only IPv4 is supported. |
| `--target-domain-name` | TARGET_DOMAIN_NAME |  | Target domain name for the Managed Microsoft AD Trust. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--direction` | one of: bidirectional, inbound, outbound, trust-direction-unspecified | BIDIRECTIONAL | Direction of the trust. Must be one of: INBOUND, OUTBOUND, BIDIRECTIONAL. Default is BIDIRECTIONAL. DIRECTION must be one of: bidirectional, inbound, outbound, trust-direction-unspecified. |
| `--handshake-secret` | HANDSHAKE_SECRET |  | Trust handshake secret with target domain. The secret will not be stored. If not specified, command will prompt user for secret. |
| `--selective-authentication` |  |  | If specified, trusted side will only have selective access to approved set of resources. Otherwise, the trusted side has forest/domain wide access. Default is false. |
| `--type` | one of: external, forest, trust-type-unspecified | FOREST | Type of the trust. Must be FOREST or EXTERNAL. Default is FOREST. TYPE must be one of: external, forest, trust-type-unspecified. |


**Examples:**
```bash
The following command creates an external, bidirectional AD trust between
my-domain.com and target-domain.com.

    $ gcloud active-directory domains trusts create my-domain.com \
        --target-domain-name=target-domain.com \
        --target-dns-ip-addresses=10.177.0.2 --type=EXTERNAL \
        --direction=BIDIRECTIONAL --selective-authentication=false \
        --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/trusts/create)

---
### `gcloud active-directory domains trusts delete`

Delete an Active Directory Trust between a Managed Microsoft AD domain and a target domain

Delete an Active Directory trust between a Managed Microsoft AD domain and
a target domain.

This command can fail for the following reasons:
  o The domain specified does not exist.
  o The active account does not have permission to access the given
    domain.
  o The AD trust specified does not exist.
  o The active account does not have permission to access the given AD
    trust.

**Synopsis:**
```
gcloud active-directory domains trusts delete DOMAIN
    --target-domain-name=TARGET_DOMAIN_NAME [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the Managed Microsoft AD domain you want to
delete a trust from. This represents a Cloud resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-domain-name` | TARGET_DOMAIN_NAME |  | Target domain name for the Managed Microsoft AD trust you want to delete. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes an AD trust between my-ad-domain.com and
my-target-domain.com.

    $ gcloud active-directory domains trusts delete my-ad-domain.com \
        --target-domain-name=my-target-domain.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/trusts/delete)

---
### `gcloud active-directory domains trusts update`

Update target DNS IP addresses for a Managed Microsoft AD trust

Update target DNS IP addresses for a Managed Microsoft AD trust between the
managed domain and the target domain.

    This command can fail for the following reasons:
      * The domain specified does not exist.
      * The active account does not have permission to access the given
        domain.
      * The AD trust specified does not exist.
      * The active account does not have permission to access the given
        AD trust.

**Synopsis:**
```
gcloud active-directory domains trusts update DOMAIN
    --target-dns-ip-addresses=[TARGET_DNS_IP_ADDRESSES,...]
    --target-domain-name=TARGET_DOMAIN_NAME [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the Managed Microsoft AD trust for which you
want to update target DNS IP Addresses. This represents a Cloud resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-dns-ip-addresses` | [TARGET_DNS_IP_ADDRESSES,...] |  | DNS server IP addresses that can resolve the target domain. Only IPv4 is supported. |
| `--target-domain-name` | TARGET_DOMAIN_NAME |  | Target domain name for the Managed Microsoft AD trust you want to update. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command updates the target DNS IP address for the AD trust
between my-domain.com and my-target-domain.com to 10.177.0.3.

    $ gcloud active-directory domains trusts update my-domain.com \
        --target-domain-name=my-target-domain.com \
        --target-dns-ip-addresses=10.177.0.3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/trusts/update)

---
### `gcloud active-directory domains trusts validate-state`

Validate the state of a Managed Microsoft AD trust

Validate the state of a Managed Microsoft AD trust.

Verify that the trust has been properly created and that the
domains/forests can communicate with each other.

This command can fail for the following reasons:
  o The AD domain specified does not exist.
  o The active account does not have permission to access the given AD
    domain.
  o The AD trust specified does not exist.
  o The active account does not have permission to access the given AD
    trust.

**Synopsis:**
```
gcloud active-directory domains trusts validate-state DOMAIN
    --target-domain-name=TARGET_DOMAIN_NAME [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Domain resource - Name of the the Managed Microsoft AD trust for which you
want to validate state. This represents a Cloud resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument domain on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DOMAIN
     ID of the domain or fully qualified identifier for the domain.

     To set the domain attribute:
     + provide the argument domain on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-domain-name` | TARGET_DOMAIN_NAME |  | Target domain name of the Managed Microsoft AD Active Directory trust you want to validate. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command validates state for an AD trust with the given target
domain name my-target-domain.com.

    $ gcloud active-directory domains trusts validate-state \
        my-domain.com --target-domain-name=my-target-domain.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/domains/trusts/validate-state)

---