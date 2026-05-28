# gcloud pam entitlements

manage Privileged Access Manager entitlements

### `gcloud pam entitlements create`

Create a new Privileged Access Manager entitlement

Create a new Privileged Access Manager (PAM) entitlement in a
project/folder/organization location.

**Synopsis:**
```
gcloud pam entitlements create
    (ENTITLEMENT
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    --entitlement-file=PATH_TO_FILE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entitlement resource - Name of the entitlement to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument entitlement on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [privilegedaccessmanager.projects.locations.entitlements,
   privilegedaccessmanager.folders.locations.entitlements,
   privilegedaccessmanager.organizations.locations.entitlements].

This must be specified.

  ENTITLEMENT
     ID of the entitlement or fully qualified identifier for the
     entitlement.

     To set the entitlement attribute:
     + provide the argument entitlement on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     The name of the folder

     To set the folder attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.folders.locations.entitlements].

  --location=LOCATION
     The resource location

     To set the location attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The name of the organization

     To set the organization attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.organizations.locations.entitlements].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--entitlement-file` | PATH_TO_FILE |  | YAML file containing the configuration of the entitlement. Use a full or relative path to a local file containing the value of entitlement_file. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command creates a new entitlement with a name of
sample-entitlement, in a project named sample-project, in location global,
and the entitlement configuration stored in a file named
sample-entitlement.yaml:

    $ gcloud pam entitlements create sample-entitlement \
        --project=sample-project --location=global \
        --entitlement-file=sample-entitlement.yaml

The following command creates a new entitlement with a name of
sample-entitlement, in a folder with ID FOLDER_ID, in location global, and
the entitlement configuration stored in a file named
sample-entitlement.yaml:

    $ gcloud pam entitlements create sample-entitlement \
        --folder=FOLDER_ID --location=global \
        --entitlement-file=sample-entitlement.yaml

The following command creates a new entitlement with a name of
sample-entitlement, in an organization with ID ORGANIZATION_ID, in location
global, and the entitlement configuration stored in a file named
sample-entitlement.yaml:

    $ gcloud pam entitlements create sample-entitlement \
        --organization=ORGANIZATION_ID --location=global \
        --entitlement-file=sample-entitlement.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/entitlements/create)

---
### `gcloud pam entitlements delete`

Delete a Privileged Access Manager entitlement

Delete a Privileged Access Manager (PAM) entitlement along with all grants
associated with it.

This command can fail for the following reasons:
  o There are non-terminal grants under the entitlement.

**Synopsis:**
```
gcloud pam entitlements delete
    (ENTITLEMENT
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entitlement resource - Name of the entitlement to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument entitlement on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [privilegedaccessmanager.projects.locations.entitlements,
   privilegedaccessmanager.folders.locations.entitlements,
   privilegedaccessmanager.organizations.locations.entitlements].

This must be specified.

  ENTITLEMENT
     ID of the entitlement or fully qualified identifier for the
     entitlement.

     To set the entitlement attribute:
     + provide the argument entitlement on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     The name of the folder

     To set the folder attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.folders.locations.entitlements].

  --location=LOCATION
     The resource location

     To set the location attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The name of the organization

     To set the organization attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.organizations.locations.entitlements].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes an entitlement with a name of
sample-entitlement, in a project named sample-project, and in location
global:

    $ gcloud pam entitlements delete sample-entitlement \
        --project=sample-project --location=global

The following command deletes an entitlement with a name of
sample-entitlement, in a folder with ID FOLDER_ID, and in location global:

    $ gcloud pam entitlements delete sample-entitlement \
        --folder=FOLDER_ID --location=global

The following command deletes an entitlement with a name of
sample-entitlement, in an organization with ID ORGANIZATION_ID, and in
location global:

    $ gcloud pam entitlements delete sample-entitlement \
        --organization=ORGANIZATION_ID --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/entitlements/delete)

---
### `gcloud pam entitlements describe`

Show details of a Privileged Access Manager entitlement

Show details of a Privileged Access Manager (PAM) entitlement.

**Synopsis:**
```
gcloud pam entitlements describe
    (ENTITLEMENT
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entitlement resource - Name of the entitlement to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument entitlement on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [privilegedaccessmanager.projects.locations.entitlements,
   privilegedaccessmanager.folders.locations.entitlements,
   privilegedaccessmanager.organizations.locations.entitlements].

This must be specified.

  ENTITLEMENT
     ID of the entitlement or fully qualified identifier for the
     entitlement.

     To set the entitlement attribute:
     + provide the argument entitlement on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     The name of the folder

     To set the folder attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.folders.locations.entitlements].

  --location=LOCATION
     The resource location

     To set the location attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The name of the organization

     To set the organization attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.organizations.locations.entitlements].
```

**Examples:**
```bash
The following command describes an entitlement with a name of
sample-entitlement, in a project named sample-project, and in location
global:

    $ gcloud pam entitlements describe sample-entitlement \
        --project=sample-project --location=global

The following command describes an entitlement with a name of
sample-entitlement, in a folder with ID FOLDER_ID, and in location global:

    $ gcloud pam entitlements describe sample-entitlement \
        --folder=FOLDER_ID --location=global

The following command describes an entitlement with a name of
sample-entitlement, in an organization with ID ORGANIZATION_ID, and in
location global:

    $ gcloud pam entitlements describe sample-entitlement \
        --organization=ORGANIZATION_ID --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/entitlements/describe)

---
### `gcloud pam entitlements export`

Export a Privileged Access Manager entitlement into a local YAML file

Export a Privileged Access Manager (PAM) entitlement into a local YAML
file.

**Synopsis:**
```
gcloud pam entitlements export
    (ENTITLEMENT
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entitlement resource - Name of the entitlement to export. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument entitlement on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [privilegedaccessmanager.projects.locations.entitlements,
   privilegedaccessmanager.folders.locations.entitlements,
   privilegedaccessmanager.organizations.locations.entitlements].

This must be specified.

  ENTITLEMENT
     ID of the entitlement or fully qualified identifier for the
     entitlement.

     To set the entitlement attribute:
     + provide the argument entitlement on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     The name of the folder

     To set the folder attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.folders.locations.entitlements].

  --location=LOCATION
     The resource location

     To set the location attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The name of the organization

     To set the organization attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.organizations.locations.entitlements].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
The following command exports an entitlement with a name of
sample-entitlement, in a project named sample-project, and in location
global to a local YAML file named sample-entitlement.yaml:

    $ gcloud pam entitlements export sample-entitlement \
        --project=sample-project --location=global \
        --destination=sample-entitlement.yaml

The following command exports an entitlement with a name of
sample-entitlement, in a folder with ID FOLDER_ID, and in location global
to a local YAML file named sample-entitlement.yaml:

    $ gcloud pam entitlements export sample-entitlement \
        --folder=FOLDER_ID --location=global \
        --destination=sample-entitlement.yaml

The following command exports an entitlement with a name of
sample-entitlement, in an organization with ID ORGANIZATION_ID, and in
location global to a local YAML file named sample-entitlement.yaml:

    $ gcloud pam entitlements export sample-entitlement \
        --organization=ORGANIZATION_ID --location=global \
        --destination=sample-entitlement.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/entitlements/export)

---
### `gcloud pam entitlements list`

List all Privileged Access Manager entitlements under a parent

List all Privileged Access Manager (PAM) entitlements in a
project/folder/organization location.

**Synopsis:**
```
gcloud pam entitlements list
    (--location=LOCATION : --folder=FOLDER --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--folder` | FOLDER |  | _[This must be specified.]_ The name of the folder To set the folder attribute: + provide the argument --location on the command line with a fully specified name; + provide the argument --folder on the command line. Must be specified for resource of type [privilegedaccessmanager.folders.locations]. |
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ The name of the organization To set the organization attribute: + provide the argument --location on the command line with a fully specified name; + provide the argument --organization on the command line. Must be specified for resource of type [privilegedaccessmanager.organizations.locations]. |


**Examples:**
```bash
The following command lists all entitlements in a project named
sample-project and in location global:

    $ gcloud pam entitlements list --project=sample-project \
        --location=global

The following command lists all entitlements in a folder with ID FOLDER_ID
and in location global:

    $ gcloud pam entitlements list --folder=FOLDER_ID --location=global

The following command lists all entitlements in an organization with ID
ORGANIZATION_ID and in location global:

    $ gcloud pam entitlements list --organization=ORGANIZATION_ID \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/entitlements/list)

---
### `gcloud pam entitlements search`

Search and list all Privileged Access Manager entitlements in a parent for which you are a requester/approver

Search and list all Privileged Access Manager (PAM) entitlements in a
project/folder/organization location for which you are a
requester/approver.

**Synopsis:**
```
gcloud pam entitlements search --caller-access-type=CALLER_ACCESS_TYPE
    (--location=LOCATION : --folder=FOLDER --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--caller-access-type` | one of: grant-approver, grant-requester |  | Search for entitlements based on whether you are a requester or approver. CALLER_ACCESS_TYPE must be one of: grant-approver, grant-requester. |


**Examples:**
```bash
The following command searches for and lists all entitlements for which you
are a requester, in a project named sample-project, and in location global:

    $ gcloud pam entitlements search --project=sample-project \
        --location=global --caller-access-type=grant-requester

The following command searches for and lists all entitlements for which you
are an approver, in a project named sample-project, and in location global:

    $ gcloud pam entitlements search --project=sample-project \
        --location=global --caller-access-type=grant-approver

The following command searches for and lists all entitlements for which you
are a requester, in a folder with ID FOLDER_ID, and in location global:

    $ gcloud pam entitlements search --folder=FOLDER_ID \
        --location=global --caller-access-type=grant-requester

The following command searches for and lists all entitlements for which you
are an approver, in a folder with ID FOLDER_ID, and in location global:

    $ gcloud pam entitlements search --folder=FOLDER_ID \
        --location=global --caller-access-type=grant-approver

The following command searches for and lists all entitlements for which you
are a requester, in an organization with ID ORGANIZATION_ID, and in
location global:

    $ gcloud pam entitlements search --organization=ORGANIZATION_ID \
        --location=global --caller-access-type=grant-requester

The following command searches for and lists all entitlements for which you
are an approver, in an organization with ID ORGANIZATION_ID, and in
location global:

    $ gcloud pam entitlements search --organization=ORGANIZATION_ID \
        --location=global --caller-access-type=grant-approver
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/entitlements/search)

---
### `gcloud pam entitlements update`

Update an existing Privileged Access Manager entitlement

Update an existing Privileged Access Manager (PAM) entitlement.

**Synopsis:**
```
gcloud pam entitlements update
    (ENTITLEMENT
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    --entitlement-file=PATH_TO_FILE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entitlement resource - Name of the entitlement to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument entitlement on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [privilegedaccessmanager.projects.locations.entitlements,
   privilegedaccessmanager.folders.locations.entitlements,
   privilegedaccessmanager.organizations.locations.entitlements].

This must be specified.

  ENTITLEMENT
     ID of the entitlement or fully qualified identifier for the
     entitlement.

     To set the entitlement attribute:
     + provide the argument entitlement on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     The name of the folder

     To set the folder attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.folders.locations.entitlements].

  --location=LOCATION
     The resource location

     To set the location attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The name of the organization

     To set the organization attribute:
     + provide the argument entitlement on the command line with a fully
       specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.organizations.locations.entitlements].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--entitlement-file` | PATH_TO_FILE |  | YAML file containing the new configuration of the entitlement. Use a full or relative path to a local file containing the value of entitlement_file. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command updates an entitlement with a name of
sample-entitlement, in a project named sample-project, in location global,
and the new entitlement configuration stored in a file named
sample-entitlement.yaml:

    $ gcloud pam entitlements update sample-entitlement \
        --project=sample-project --location=global \
        --entitlement-file=sample-entitlement.yaml

The following command updates an entitlement with a name of
sample-entitlement, in a folder with ID FOLDER_ID, in location global, and
the new entitlement configuration stored in a file named
sample-entitlement.yaml:

    $ gcloud pam entitlements update sample-entitlement \
        --folder=FOLDER_ID --location=global \
        --entitlement-file=sample-entitlement.yaml

The following command updates an entitlement with a name of
sample-entitlement, in an organization with ID ORGANIZATION_ID, in location
global, and the new entitlement configuration stored in a file named
sample-entitlement.yaml:

    $ gcloud pam entitlements update sample-entitlement \
        --organization=ORGANIZATION_ID --location=global \
        --entitlement-file=sample-entitlement.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/entitlements/update)

---