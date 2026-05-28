# gcloud pam operations

manage Privileged Access Manager Long Running Operations

### `gcloud pam operations delete`

Delete a Privileged Access Manager long running operation

Delete a Privileged Access Manager (PAM) long running operation.

**Synopsis:**
```
gcloud pam operations delete
    (OPERATION
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Name of the operation to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [privilegedaccessmanager.projects.locations.operations,
   privilegedaccessmanager.folders.locations.operations,
   privilegedaccessmanager.organizations.locations.operations].

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     The name of the folder

     To set the folder attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.folders.locations.operations].

  --location=LOCATION
     The resource location

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The name of the organization

     To set the organization attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.organizations.locations.operations].
```

**Examples:**
```bash
The following command deletes an operation with the full name
OPERATION_NAME:

    $ gcloud pam operations delete OPERATION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/operations/delete)

---
### `gcloud pam operations describe`

Show details of a Privileged Access Manager long running operation

Show details of a Privileged Access Manager (PAM) long running operation.

**Synopsis:**
```
gcloud pam operations describe
    (OPERATION
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Name of the operation to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [privilegedaccessmanager.projects.locations.operations,
   privilegedaccessmanager.folders.locations.operations,
   privilegedaccessmanager.organizations.locations.operations].

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     The name of the folder

     To set the folder attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.folders.locations.operations].

  --location=LOCATION
     The resource location

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The name of the organization

     To set the organization attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.organizations.locations.operations].
```

**Examples:**
```bash
The following command describes an operation with the full name
OPERATION_NAME:

    $ gcloud pam operations describe OPERATION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/operations/describe)

---
### `gcloud pam operations list`

List all Privileged Access Manager long running operations under a location

List all Privileged Access Manager (PAM) long running operations under a
project/folder/organization location.

**Synopsis:**
```
gcloud pam operations list
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
The following command lists all operations in a project named
sample-project and in location global:

    $ gcloud pam operations list --project=sample-project \
        --location=global

The following command lists all operations in a folder with ID FOLDER_ID
and in location global:

    $ gcloud pam operations list --folder=FOLDER_ID --location=global

The following command lists all operations in an organization with ID
ORGANIZATION_ID and in location global:

    $ gcloud pam operations list --organization=ORGANIZATION_ID \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/operations/list)

---
### `gcloud pam operations wait`

Poll a Privileged Access Manager long running operation

Poll a Privileged Access Manager (PAM) long running operation until it
completes and then display its result.

**Synopsis:**
```
gcloud pam operations wait
    (OPERATION
      : --folder=FOLDER --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Name of the operation to poll. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types:
   [privilegedaccessmanager.projects.locations.operations,
   privilegedaccessmanager.folders.locations.operations,
   privilegedaccessmanager.organizations.locations.operations].

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     The name of the folder

     To set the folder attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.folders.locations.operations].

  --location=LOCATION
     The resource location

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The name of the organization

     To set the organization attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type
       [privilegedaccessmanager.organizations.locations.operations].
```

**Examples:**
```bash
The following command polls an operation with the full name OPERATION_NAME:

    $ gcloud pam operations wait OPERATION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/operations/wait)

---