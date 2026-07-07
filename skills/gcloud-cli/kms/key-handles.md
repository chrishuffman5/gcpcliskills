# gcloud kms key-handles

create and manage KeyHandle resources

### `gcloud kms key-handles create`

Create a new KeyHandle

Creates a new KeyHandle, triggering the provisioning of a new CryptoKey for
CMEK use with the given resource type in the configured key project and the
same location

**Synopsis:**
```
gcloud kms key-handles create --location=LOCATION
    --resource-type=RESOURCE_TYPE
    (--generate-key-handle-id | --key-handle-id=KEY_HANDLE_ID)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |
| `--resource-type` | RESOURCE_TYPE |  | _[This must be specified.]_ The resource type selector for KeyHandle resources of the form {SERVICE}.{UNIVERSE_DOMAIN}/{TYPE}. |
| `--generate-key-handle-id` |  |  | _[Exactly one of these must be specified:]_ Generate a KeyHandle id for the new KeyHandle resource. |
| `--key-handle-id` | KEY_HANDLE_ID |  | _[Exactly one of these must be specified:]_ The KeyHandle id for the new KeyHandle resource. |


**Examples:**
```bash
The following command creates a KeyHandle named my-key-handle within the
location global for the resource type compute.googleapis.com/Disk:

    $ gcloud kms key-handles create --key-handle-id=my-key-handle \
        --my-key-handle --location=global \
        --resource-type=compute.googleapis.com/Disk

In case we want to generate a random KeyHandle id, we can use the
--generate-key-handle-id flag instead of the --key-handle-id flag.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/key-handles/create)

---
### `gcloud kms key-handles describe`

Get metadata for a KeyHandle

Get metadata for a KeyHandle.

**Synopsis:**
```
gcloud kms key-handles describe (KEY_HANDLE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key handle resource - The KeyHandle to get metadata for. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument key_handle on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEY_HANDLE
     ID of the key handle or fully qualified identifier for the key
     handle.

     To set the key_handle attribute:
     + provide the argument key_handle on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resource.

     To set the location attribute:
     + provide the argument key_handle on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command gets metadata for a KeyHandle named my-key-handle in
the locations us-central1.

    $ gcloud kms key-handles describe my-key-handle \
         --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/key-handles/describe)

---
### `gcloud kms key-handles list`

List KeyHandle resources within a project and location

Lists all KeyHandle resources within a given project and location.
Addtionally, can filter the list.

**Synopsis:**
```
gcloud kms key-handles list --location=LOCATION
    --resource-type=RESOURCE_TYPE [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |
| `--resource-type` | RESOURCE_TYPE |  | _[This must be specified.]_ The resource type selector for KeyHandle resources of the form {SERVICE}.{UNIVERSE_DOMAIN}/{TYPE}. |


**Examples:**
```bash
The following command lists a maximum of five KeyHandle resources in the
location global:

    $ gcloud kms key-handles list --location=global --limit=5

The following command lists all KeyHandle resources in the location global
that have a resource type selector of compute.googleapis.com/Instance:

    $ gcloud kms key-handles list --location=global \
        --resource-type=compute.googleapis.com/Instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/key-handles/list)

---