# gcloud edge-cache keysets

interact with and manage EdgeCacheKeyset resources

### `gcloud edge-cache keysets create`

Create an EdgeCacheKeyset resource

Create a new EdgeCacheKeyset resource.

**Synopsis:**
```
gcloud edge-cache keysets create (KEYSET : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--public-key=[id=ID],[managed=MANAGED],[value=VALUE]]
    [--validation-shared-key=[secret_version=SECRET_VERSION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Keyset resource - The name of the EdgeCacheKeyset resource to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument keyset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEYSET
     ID of the keyset or fully qualified identifier for the keyset.

     To set the keyset attribute:
     + provide the argument keyset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument keyset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Human-readable description of the resource. |
| `--labels` | [KEY=VALUE,...] |  | List of KEY=VALUE labels to attach to this resource. |
| `--public-key` | [id=ID],[managed=MANAGED],[value=VALUE] |  | Set of public keys to use for validating signed requests, when associated with a route. This flag can be repeated to create a Keyset with multiple public keys. If you are providing your own public keys, specify the key in the form id=ID,value=BASE64ENCODEDPUBLICKEY. If you are using Google-managed public keys as part of a dual-token setup, specify the key in the form id=ID,managed=true. id id (name) name of the key within the keyset. value URL-safe base64 encoded public key. Cannot be specified if managed=true. managed Boolean indicating this is a Google-managed key. Cannot be specified if value=true. To create a public key with id 'foo', pass --public-key='id=foo,value=VALUE' to gcloud edge-cache keysets create. To create a Google-managed public key with id 'bar', pass --public-key='id=foo,managed=true' to gcloud edge-cache keysets create. At least one of public-key or validation-shared-key must be specified. |
| `--validation-shared-key` | [secret_version=SECRET_VERSION] |  | An ordered list of shared keys to use for validating signed requests. To create a validation shared key pointing to a Secret Manager secret version with name projects/PROJECT/secrets/SECRET/versions/VERSION, pass --validation-shared-key='secret_version=projects/PROJECT/secrets/SECRET/versions/VERSION' to gcloud edge-cache keysets create. secret_version The name of the secret in Secret Manager. Must be in the format projects/PROJECT/secrets/SECRET/versions/VERSION. At least one of public-key or validation-shared-key must be specified. |


**Examples:**
```bash
To create an EdgeCacheKeyset resource called 'my-keyset', run:

    $ gcloud edge-cache keysets create my-keyset \
        --public-key='id=KEYID,value=BASE64PUBLICKEY'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/keysets/create)

---
### `gcloud edge-cache keysets delete`

Delete an EdgeCacheKeyset resource

Delete an EdgeCacheKeyset resource.

**Synopsis:**
```
gcloud edge-cache keysets delete (KEYSET : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Keyset resource - The name of the EdgeCacheKeyset resource to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument keyset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEYSET
     ID of the keyset or fully qualified identifier for the keyset.

     To set the keyset attribute:
     + provide the argument keyset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument keyset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an EdgeCacheKeyset resource called 'my-keyset', run:

    $ gcloud edge-cache keysets delete my-keyset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/keysets/delete)

---
### `gcloud edge-cache keysets describe`

Show details about an EdgeCacheKeyset resource

Show details about an EdgeCacheKeyset resource.

**Synopsis:**
```
gcloud edge-cache keysets describe (KEYSET : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Keyset resource - The EdgeCacheKeyset resource you want to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument keyset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEYSET
     ID of the keyset or fully qualified identifier for the keyset.

     To set the keyset attribute:
     + provide the argument keyset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument keyset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Examples:**
```bash
To show details for an EdgeCacheKeyset resource named 'my-keyset', run:

    $ gcloud edge-cache keysets describe my-keyset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/keysets/describe)

---
### `gcloud edge-cache keysets export`

Export an EdgeCacheKeyset resource

Export an EdgeCacheKeyset resource to YAML.

**Synopsis:**
```
gcloud edge-cache keysets export (KEYSET : --location=LOCATION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Keyset resource - The EdgeCacheKeyset resource you want to export. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument keyset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEYSET
     ID of the keyset or fully qualified identifier for the keyset.

     To set the keyset attribute:
     + provide the argument keyset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument keyset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export an EdgeCacheKeyset resourced named 'my-keyset', run:

    $ gcloud edge-cache keysets export my-keyset \
        --destination=keyset.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/keysets/export)

---
### `gcloud edge-cache keysets import`

Import an EdgeCacheKeyset resource

Import an EdgeCacheKeyset resource. If the named EdgeCacheKeyset resource
already exists, the resource will be updated to match the imported resource
configuration.

Note: If you are updating an existing EdgeCacheKeyset resource, you should
ensure that it includes any public keys still needed to validate incoming
user requests.

If the named EdgeCacheKeyset resource does not already exist, a new
EdgeCacheKeyset resource will be created with that name.

**Synopsis:**
```
gcloud edge-cache keysets import (KEYSET : --location=LOCATION) [--async]
    [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Keyset resource - The EdgeCacheKeyset resource you want to import. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument keyset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEYSET
     ID of the keyset or fully qualified identifier for the keyset.

     To set the keyset attribute:
     + provide the argument keyset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument keyset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Path to a YAML file containing the configuration export data. The YAML file must not contain any output-only fields. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... $CLOUDSDKROOT is can be obtained with the following command: $ gcloud info --format='value(installation.sdk_root)' |


**Examples:**
```bash
To import an EdgeCacheKeyset resource named 'my-keyset' from a YAML file,
run:

    $ gcloud edge-cache keysets import my-keyset --source=my-keyset.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/keysets/import)

---
### `gcloud edge-cache keysets list`

List EdgeCacheKeyset resources

List EdgeCacheKeyset resources.

**Synopsis:**
```
gcloud edge-cache keysets list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list existing EdgeCacheKeyset resources, run:

    $ gcloud edge-cache keysets list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/keysets/list)

---
### `gcloud edge-cache keysets update`

Update an EdgeCacheKeyset resource

Update an existing EdgeCacheKeyset resource.

**Synopsis:**
```
gcloud edge-cache keysets update (KEYSET : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--public-key=[id=ID],[managed=MANAGED],[value=VALUE]]
    [--validation-shared-key=[secret_version=SECRET_VERSION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Keyset resource - The name of the EdgeCacheKeyset resource to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument keyset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEYSET
     ID of the keyset or fully qualified identifier for the keyset.

     To set the keyset attribute:
     + provide the argument keyset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument keyset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Human-readable description of the resource. |
| `--labels` | [KEY=VALUE,...] |  | List of KEY=VALUE labels to attach to this resource. |
| `--public-key` | [id=ID],[managed=MANAGED],[value=VALUE] |  | Set of public keys to use for validating signed requests, when associated with a route. This flag can be repeated to create a Keyset with multiple public keys. If you are providing your own public keys, specify the key in the form id=ID,value=BASE64ENCODEDPUBLICKEY. If you are using Google-managed public keys as part of a dual-token setup, specify the key in the form id=ID,managed=true. id id (name) name of the key within the keyset. value URL-safe base64 encoded public key. Cannot be specified if managed=true. managed Boolean indicating this is a Google-managed key. Cannot be specified if value=true. To create a public key with id 'foo', pass --public-key='id=foo,value=VALUE' to gcloud edge-cache keysets update. To create a Google-managed public key with id 'bar', pass --public-key='id=foo,managed=true' to gcloud edge-cache keysets update. At least one of public-key or validation-shared-key must be specified. |
| `--validation-shared-key` | [secret_version=SECRET_VERSION] |  | An ordered list of shared keys to use for validating signed requests. To create a validation shared key pointing to a Secret Manager secret version with name projects/PROJECT/secrets/SECRET/versions/VERSION, pass --validation-shared-key='secret_version=projects/PROJECT/secrets/SECRET/versions/VERSION' to gcloud edge-cache keysets update. secret_version The name of the secret in Secret Manager. Must be in the format projects/PROJECT/secrets/SECRET/versions/VERSION. At least one of public-key or validation-shared-key must be specified. |


**Examples:**
```bash
To update an EdgeCacheKeyset resource called 'my-keyset', run:

    $ gcloud edge-cache keysets update my-keyset \
        --public-key='id=KEYID,value=BASE64PUBLICKEY'

The update command appends keys to an existing EdgeCacheKeyset resource. To
add more than one key to an EdgeCacheKeyset resource, provide multiple
--public-key values:

    $ gcloud edge-cache keysets update my-keyset \
        --public-key='id=KEYID,value=BASE64PUBLICKEY' \
        --public-key='id=EXISTING,value=EXISTINGPUBLICKEY'

You can specify, and an EdgeCacheKeyset resource can contain, up to three
(3) public keys. To delete unused public keys within an existing Keyset,
use the import command to specify the EdgeCacheKeyset resource in full,
omitting any unused publicKey items.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/keysets/update)

---