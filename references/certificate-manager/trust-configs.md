# gcloud certificate-manager trust-configs

manage Certificate Manager trust configs

### `gcloud certificate-manager trust-configs create`

Create TrustConfig

Create a TrustConfig.

**Synopsis:**
```
gcloud certificate-manager trust-configs create
    (TRUST_CONFIG : --location=LOCATION)
    (--allowlisted-certificates=[ALLOWLISTED_CERTIFICATES,...]
      --trust-store=[intermediate-cas=INTERMEDIATE-CAS],
      [trust-anchors=TRUST-ANCHORS]) [--async] [--description=DESCRIPTION]
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TrustConfig resource - Name of the TrustConfig to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument trust_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRUST_CONFIG
     ID of the trustConfig or fully qualified identifier for the
     trustConfig.

     To set the trust_config attribute:
     + provide the argument trust_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument trust_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowlisted-certificates` | [ALLOWLISTED_CERTIFICATES,...] |  | _[At least one of these must be specified:]_ Allowlisted PEM-encoded certificates. Certificates should be provided in files. For multiple file names, separate them by a comma (','). One file can contain multiple certificates. Examples: Single file: --allowlisted-certificates=ac.pem Multiple files: --allowlisted-certificates=ac1.pem,ac2.pem |
| `--trust-store` | [intermediate-cas=INTERMEDIATE-CAS],[trust-anchors=TRUST-ANCHORS] |  | _[At least one of these must be specified:]_ Trust Store with the given trust anchor and intermediate CA PEM-encoded certificates. Certificates should be provided in files. For multiple file names, separate them by a semicolon (';') and quote them ('"'). One file can contain multiple certificates. Intermediate CAs are optional. Examples: Single files: --trust-store trust-anchors=ta.pem,intermediate-cas=ica.pem No intermediate CAs: --trust-store trust-anchors=ta.pem Multiple files: --trust-store trust-anchors="ta1.pem;ta2.pem",intermediate-cas="ica1.pem;ica2.pem" |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Human-readable description of the resource. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a TrustConfig from PEM certificate files, run:

    $ gcloud certificate-manager trust-configs create my-trust-config \
        --description="my description" \
        --labels=my-key1=my-value1,my-key2=my-value2 \
        --trust-store=trust-anchors=ta.pem,\
    intermediate-cas="ica1.pem;ica2.pem"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/trust-configs/create)

---
### `gcloud certificate-manager trust-configs delete`

Delete TrustConfig

Delete the specified TrustConfig.

**Synopsis:**
```
gcloud certificate-manager trust-configs delete
    (TRUST_CONFIG : --location=LOCATION) [--async] [--etag=ETAG]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TrustConfig resource - Name of the TrustConfig you want to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument trust_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRUST_CONFIG
     ID of the trustConfig or fully qualified identifier for the
     trustConfig.

     To set the trust_config attribute:
     + provide the argument trust_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument trust_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | The current etag of the asset. If an etag is provided and does not match the current etag of the asset, the deletion will be blocked. |


**Examples:**
```bash
To delete a TrustConfig called 'my-trust-config', run:

    $ gcloud certificate-manager trust-configs delete my-trust-config \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/trust-configs/delete)

---
### `gcloud certificate-manager trust-configs describe`

Show details about a TrustConfig

Show details about a TrustConfig.

**Synopsis:**
```
gcloud certificate-manager trust-configs describe
    (TRUST_CONFIG : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TrustConfig resource - The TrustConfig you want to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument trust_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRUST_CONFIG
     ID of the trustConfig or fully qualified identifier for the
     trustConfig.

     To set the trust_config attribute:
     + provide the argument trust_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument trust_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Examples:**
```bash
To show details about an existing trust config, run:

    $ gcloud certificate-manager trust-configs describe my-trust-config
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/trust-configs/describe)

---
### `gcloud certificate-manager trust-configs export`

Export TrustConfig

Export a TrustConfig.

**Synopsis:**
```
gcloud certificate-manager trust-configs export
    (TRUST_CONFIG : --location=LOCATION) [--destination=DESTINATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TrustConfig resource - Name of the TrustConfig to export. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument trust_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRUST_CONFIG
     ID of the trustConfig or fully qualified identifier for the
     trustConfig.

     To set the trust_config attribute:
     + provide the argument trust_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument trust_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export a TrustConfig, run:

    $ gcloud certificate-manager trust-configs export my-trust-config \
        --destination=my-trust-config.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/trust-configs/export)

---
### `gcloud certificate-manager trust-configs import`

Import TrustConfig

Import a TrustConfig.

**Synopsis:**
```
gcloud certificate-manager trust-configs import
    (TRUST_CONFIG : --location=LOCATION) [--async] [--source=SOURCE]
    [--update-mask=UPDATE_MASK] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TrustConfig resource - Name of the TrustConfig to import. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument trust_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRUST_CONFIG
     ID of the trustConfig or fully qualified identifier for the
     trustConfig.

     To set the trust_config attribute:
     + provide the argument trust_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument trust_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Path to a YAML file containing the configuration export data. The YAML file must not contain any output-only fields. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... $CLOUDSDKROOT is can be obtained with the following command: $ gcloud info --format='value(installation.sdk_root)' |
| `--update-mask` | UPDATE_MASK |  | Update mask used to specify fields to be overwritten in the TrustConfig by import. TrustConfig must already exist. Fields specified in the update-mask are relative to the TrustConfig. The flag can be a comma-separated list of updatable non-nested fields, e.g. description or trust_stores. Valid example: --update-mask=description,trust_stores. |


**Examples:**
```bash
To import a TrustConfig from a YAML file, run:

    $ gcloud certificate-manager trust-configs import my-trust-config \
        --source=my-trust-config.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/trust-configs/import)

---
### `gcloud certificate-manager trust-configs list`

List all TrustConfigs in a project

List existing TrustConfigs.

**Synopsis:**
```
gcloud certificate-manager trust-configs list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + if left empty, will use the wildcard '-' to list all locations. |


**Examples:**
```bash
To list existing TrustConfigs, run:

    $ gcloud certificate-manager trust-configs list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/trust-configs/list)

---
### `gcloud certificate-manager trust-configs update`

Update TrustConfig

Update a TrustConfig.

**Synopsis:**
```
gcloud certificate-manager trust-configs update
    (TRUST_CONFIG : --location=LOCATION)
    [--add-allowlisted-certificates=[ADD_ALLOWLISTED_CERTIFICATES,...]]
    [--async] [--description=DESCRIPTION]
    [--trust-store=[intermediate-cas=INTERMEDIATE-CAS],
      [trust-anchors=TRUST-ANCHORS]] [--update-labels=[KEY=VALUE,...]]
    [--clear-allowlisted-certificates
      | --remove-allowlisted-certificates=[REMOVE_ALLOWLISTED_CERTIFICATES,
      ...]] [--clear-labels | --remove-labels=[KEY,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TrustConfig resource - Name of the TrustConfig to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument trust_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRUST_CONFIG
     ID of the trustConfig or fully qualified identifier for the
     trustConfig.

     To set the trust_config attribute:
     + provide the argument trust_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument trust_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--add-allowlisted-certificates` | [ADD_ALLOWLISTED_CERTIFICATES,...] |  | Add allowlisted PEM-encoded certificates. Certificates should be provided in files. For multiple file names, separate them by a comma (','). One file can contain multiple certificates. Examples: Single file: --add-allowlisted-certificates=ac.pem Multiple files: --add-allowlisted-certificates=ac1.pem,ac2.pem |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Human-readable description of the resource. |
| `--trust-store` | [intermediate-cas=INTERMEDIATE-CAS],[trust-anchors=TRUST-ANCHORS] |  | Trust Store with the given trust anchor and intermediate CA PEM-encoded certificates. Certificates should be provided in files. For multiple file names, separate them by a semicolon (';') and quote them ('"'). One file can contain multiple certificates. Intermediate CAs are optional. Examples: Single files: --trust-store trust-anchors=ta.pem,intermediate-cas=ica.pem No intermediate CAs: --trust-store trust-anchors=ta.pem Multiple files: --trust-store trust-anchors="ta1.pem;ta2.pem",intermediate-cas="ica1.pem;ica2.pem" |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update a TrustConfig, run:

    $ gcloud certificate-manager trust-configs update my-trust-config \
        --description="updated description" \
        --trust-store=trust-anchors=ta.pem,\
    intermediate-cas="ica1.pem;ica2.pem" \
        --update-labels=my-key1=my-updated-value1 \
        --remove-labels=my-key2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/trust-configs/update)

---