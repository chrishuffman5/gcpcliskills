# gcloud pam grants

manage Privileged Access Manager grants

### `gcloud pam grants approve`

Approve a Privileged Access Manager grant

Approve a Privileged Access Manager (PAM) grant with a reason.

**Synopsis:**
```
gcloud pam grants approve
    (GRANT : --entitlement=ENTITLEMENT
      --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [--reason=REASON] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Grant resource - Name of the grant to approve. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument grant on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [privilegedaccessmanager.projects.locations.entitlements.grants,
   privilegedaccessmanager.folders.locations.entitlements.grants,
   privilegedaccessmanager.organizations.locations.entitlements.grants].

This must be specified.

  GRANT
     ID of the grant or fully qualified identifier for the grant.

     To set the grant attribute:
     + provide the argument grant on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entitlement=ENTITLEMENT
     The entitlement id

     To set the entitlement attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --entitlement on the command line.

  --folder=FOLDER
     The name of the folder

     To set the folder attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.folders.locations.entitlements.grants].

  --location=LOCATION
     The resource location

     To set the location attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The name of the organization

     To set the organization attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.organizations.locations.entitlements.grants].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--reason` | REASON |  | Reason for approving the grant. |


**Examples:**
```bash
The following command approves a grant with the full name GRANT_NAME and a
reason of approval reason:

    $ gcloud pam grants approve GRANT_NAME --reason="approval reason"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/grants/approve)

---
### `gcloud pam grants create`

Create a new Privileged Access Manager grant

Create a new Privileged Access Manager (PAM) grant under an entitlement.

**Synopsis:**
```
gcloud pam grants create --requested-duration=REQUESTED_DURATION
    (--entitlement=ENTITLEMENT
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [--additional-email-recipients=[ADDITIONAL_EMAIL_RECIPIENTS,...]]
    [--justification=JUSTIFICATION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--requested-duration` | REQUESTED_DURATION |  | Duration of the grant being created. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-email-recipients` | [ADDITIONAL_EMAIL_RECIPIENTS,...] |  | Additional email addresses that are notified for all actions performed on the grant. |
| `--justification` | JUSTIFICATION |  | Justification for the grant. |


**Examples:**
```bash
The following command creates a new grant against the entitlement with the
full name ENTITLEMENT_NAME, a requested duration of 1 hour 30 minutes, a
justification of some justification and two additional email recipients
abc@example.com and xyz@example.com:

    $ gcloud pam grants create --entitlement=ENTITLEMENT_NAME \
        --requested-duration=5400s \
        --justification="some justification" \
        --additional-email-recipients=abc@example.com,xyz@example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/grants/create)

---
### `gcloud pam grants deny`

Deny a Privileged Access Manager grant

Deny a Privileged Access Manager (PAM) grant with a reason.

**Synopsis:**
```
gcloud pam grants deny
    (GRANT : --entitlement=ENTITLEMENT
      --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [--reason=REASON] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Grant resource - Name of the grant to deny. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument grant on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [privilegedaccessmanager.projects.locations.entitlements.grants,
   privilegedaccessmanager.folders.locations.entitlements.grants,
   privilegedaccessmanager.organizations.locations.entitlements.grants].

This must be specified.

  GRANT
     ID of the grant or fully qualified identifier for the grant.

     To set the grant attribute:
     + provide the argument grant on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entitlement=ENTITLEMENT
     The entitlement id

     To set the entitlement attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --entitlement on the command line.

  --folder=FOLDER
     The name of the folder

     To set the folder attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.folders.locations.entitlements.grants].

  --location=LOCATION
     The resource location

     To set the location attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The name of the organization

     To set the organization attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.organizations.locations.entitlements.grants].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--reason` | REASON |  | Reason for denying the grant. |


**Examples:**
```bash
The following command denies a grant with the full name GRANT_NAME and a
reason of denial reason:

    $ gcloud pam grants deny GRANT_NAME --reason="denial reason"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/grants/deny)

---
### `gcloud pam grants describe`

Show details of a Privileged Access Manager grant

Show details of a Privileged Access Manager (PAM) grant.

**Synopsis:**
```
gcloud pam grants describe
    (GRANT : --entitlement=ENTITLEMENT
      --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Grant resource - Name of the grant to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument grant on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [privilegedaccessmanager.projects.locations.entitlements.grants,
   privilegedaccessmanager.folders.locations.entitlements.grants,
   privilegedaccessmanager.organizations.locations.entitlements.grants].

This must be specified.

  GRANT
     ID of the grant or fully qualified identifier for the grant.

     To set the grant attribute:
     + provide the argument grant on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entitlement=ENTITLEMENT
     The entitlement id

     To set the entitlement attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --entitlement on the command line.

  --folder=FOLDER
     The name of the folder

     To set the folder attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.folders.locations.entitlements.grants].

  --location=LOCATION
     The resource location

     To set the location attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The name of the organization

     To set the organization attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.organizations.locations.entitlements.grants].
```

**Examples:**
```bash
The following command describes a grant with the full name GRANT_NAME:

    $ gcloud pam grants describe GRANT_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/grants/describe)

---
### `gcloud pam grants list`

List all Privileged Access Manager grants associated with an entitlement

List all Privileged Access Manager (PAM) grants associated with an
entitlement.

**Synopsis:**
```
gcloud pam grants list
    (--entitlement=ENTITLEMENT
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--entitlement` | ENTITLEMENT |  | _[This must be specified.]_ ID of the entitlement or fully qualified identifier for the entitlement. To set the entitlement attribute: + provide the argument --entitlement on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--folder` | FOLDER |  | _[This must be specified.]_ The name of the folder To set the folder attribute: + provide the argument --entitlement on the command line with a fully specified name; + provide the argument --folder on the command line. Must be specified for resource of type [privilegedaccessmanager.folders.locations.entitlements]. |
| `--location` | LOCATION |  | _[This must be specified.]_ The resource location To set the location attribute: + provide the argument --entitlement on the command line with a fully specified name; + provide the argument --location on the command line. |
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ The name of the organization To set the organization attribute: + provide the argument --entitlement on the command line with a fully specified name; + provide the argument --organization on the command line. Must be specified for resource of type [privilegedaccessmanager.organizations.locations.entitlements]. |


**Examples:**
```bash
The following command lists all grants associated with an entitlement with
the full name ENTITLEMENT_NAME:

    $ gcloud pam grants list --entitlement=ENTITLEMENT_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/grants/list)

---
### `gcloud pam grants revoke`

Revoke a Privileged Access Manager grant

Revoke a Privileged Access Manager (PAM) grant with a reason.

**Synopsis:**
```
gcloud pam grants revoke
    (GRANT : --entitlement=ENTITLEMENT
      --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [--async] [--reason=REASON] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Grant resource - Name of the grant to revoke. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument grant on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [privilegedaccessmanager.projects.locations.entitlements.grants,
   privilegedaccessmanager.folders.locations.entitlements.grants,
   privilegedaccessmanager.organizations.locations.entitlements.grants].

This must be specified.

  GRANT
     ID of the grant or fully qualified identifier for the grant.

     To set the grant attribute:
     + provide the argument grant on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entitlement=ENTITLEMENT
     The entitlement id

     To set the entitlement attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --entitlement on the command line.

  --folder=FOLDER
     The name of the folder

     To set the folder attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.folders.locations.entitlements.grants].

  --location=LOCATION
     The resource location

     To set the location attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The name of the organization

     To set the organization attribute:
     + provide the argument grant on the command line with a fully
       specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.organizations.locations.entitlements.grants].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--reason` | REASON |  | Reason for revoking the grant. |


**Examples:**
```bash
The following command revokes a grant with the full name GRANT_NAME and a
reason of revoke reason:

    $ gcloud pam grants revoke GRANT_NAME --reason="revoke reason"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/grants/revoke)

---
### `gcloud pam grants search`

Search for and list all Privileged Access Manager grants you have created, have approved, or can approve

Search for and list all Privileged Access Manager (PAM) grants you have
created, have approved, or can approve.

**Synopsis:**
```
gcloud pam grants search --caller-relationship=CALLER_RELATIONSHIP
    (--entitlement=ENTITLEMENT
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--caller-relationship` | one of: can-approve, had-approved, had-created |  | Whether to return grants you have created, have approved, or can approve. CALLER_RELATIONSHIP must be one of: can-approve, had-approved, had-created. |


**Examples:**
```bash
The following command searches for and lists all grants you have created
which are associated with an entitlement with the full name
ENTITLEMENT_NAME:

    $ gcloud pam grants search --entitlement=ENTITLEMENT_NAME \
        --caller-relationship=had-created

The following command searches for and lists all grants you have approved
or denied which are associated with an entitlement with the full name
ENTITLEMENT_NAME:

    $ gcloud pam grants search --entitlement=ENTITLEMENT_NAME \
        --caller-relationship=had-approved

The following command searches for and lists all grants you can approve
which are associated with an entitlement with the full name
ENTITLEMENT_NAME:

    $ gcloud pam grants search --entitlement=ENTITLEMENT_NAME \
        --caller-relationship=can-approve
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/grants/search)

---