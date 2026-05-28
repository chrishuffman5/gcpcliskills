# gcloud certificate-manager issuance-configs

manage Certificate Manager Certificate Issuance Configs

### `gcloud certificate-manager issuance-configs create`

Create a Certificate Issuance Config

Create a new Certificate Issuance Config.

**Synopsis:**
```
gcloud certificate-manager issuance-configs create
    (CERTIFICATE_ISSUANCE_CONFIG : --location=LOCATION) --ca-pool=CA_POOL
    [--async] [--description=DESCRIPTION]
    [--key-algorithm=KEY_ALGORITHM; default="rsa-2048"]
    [--labels=[KEY=VALUE,...]] [--lifetime=LIFETIME; default="P30D"]
    [--rotation-window-percentage=ROTATION_WINDOW_PERCENTAGE; default=66]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CertificateIssuanceConfig resource - Name of the Certificate Issuance
Config to create. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument certificate_issuance_config on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_ISSUANCE_CONFIG
     ID of the certificateIssuanceConfig or fully qualified identifier for
     the certificateIssuanceConfig.

     To set the certificate_issuance_config attribute:
     + provide the argument certificate_issuance_config on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument certificate_issuance_config on the command
       line with a fully specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ca-pool` | CA_POOL |  | CA Pool used for issuing certificates. For example: $ gcloud certificate-manager issuance-configs create \ --ca-pool=projects/test-project/locations/us-west1/caPools/\ my-ca-pool |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Human-readable description of the resource. |
| `--key-algorithm` | one of: ecdsa-p256, rsa-2048 | rsa-2048 | Key algorithm to use when generating the private key. Defaults to rsa-2048. KEY_ALGORITHM must be one of: ecdsa-p256, rsa-2048. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--lifetime` | LIFETIME | P30D | Lifetime of issued certificates in ISO 8601 format. Use gcloud topic datetimes for details. Defaults to P30D. |
| `--rotation-window-percentage` | ROTATION_WINDOW_PERCENTAGE | 66 | How long along the lifetime of the ceritificate to renew, expressed as a percentage. Defaults to 66. |


**Examples:**
```bash
To create a Certificate Issuance Config called my-cic, run:

    $ gcloud certificate-manager issuance-configs create my-cic \
        --ca-pool=my-ca-pool
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/issuance-configs/create)

---
### `gcloud certificate-manager issuance-configs delete`

Delete a Certificate Issuance Config

Delete a Certificate Issuance Config.

**Synopsis:**
```
gcloud certificate-manager issuance-configs delete
    (CERTIFICATE_ISSUANCE_CONFIG : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CertificateIssuanceConfig resource - Name of the CertificateIssuanceConfig
to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument certificate_issuance_config on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_ISSUANCE_CONFIG
     ID of the certificateIssuanceConfig or fully qualified identifier for
     the certificateIssuanceConfig.

     To set the certificate_issuance_config attribute:
     + provide the argument certificate_issuance_config on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument certificate_issuance_config on the command
       line with a fully specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a Certificate Issuance Config called my-cic, run:

    $ gcloud certificate-manager issuance-configs delete my-cic
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/issuance-configs/delete)

---
### `gcloud certificate-manager issuance-configs describe`

Show details about a Certificate Issuance Config

Show details about a Certificate Issuance Config.

**Synopsis:**
```
gcloud certificate-manager issuance-configs describe
    (CERTIFICATE_ISSUANCE_CONFIG : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CertificateIssuanceConfig resource - CertificateIssuanceConfig you want to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument certificate_issuance_config on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_ISSUANCE_CONFIG
     ID of the certificateIssuanceConfig or fully qualified identifier for
     the certificateIssuanceConfig.

     To set the certificate_issuance_config attribute:
     + provide the argument certificate_issuance_config on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument certificate_issuance_config on the command
       line with a fully specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Examples:**
```bash
To show details about an existing Certificate Issuance Config my-cic, run:

    $ gcloud certificate-manager issuance-configs describe my-cic
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/issuance-configs/describe)

---
### `gcloud certificate-manager issuance-configs list`

List all Certificate Issuance Configs in a project

List existing Certificate Issuance Configs.

**Synopsis:**
```
gcloud certificate-manager issuance-configs list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + if left empty, will use the wildcard '-' to list all locations. |


**Examples:**
```bash
To list existing Certificate Issuance Configs, run:

    $ gcloud certificate-manager issuance-configs list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/issuance-configs/list)

---
### `gcloud certificate-manager issuance-configs update`

Update a Certificate Issuance Config

Update a Certificate Issuance Config.

**Synopsis:**
```
gcloud certificate-manager issuance-configs update
    (CERTIFICATE_ISSUANCE_CONFIG : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CertificateIssuanceConfig resource - Name of the Certificate Issuance
Config to update. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument certificate_issuance_config on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_ISSUANCE_CONFIG
     ID of the certificateIssuanceConfig or fully qualified identifier for
     the certificateIssuanceConfig.

     To set the certificate_issuance_config attribute:
     + provide the argument certificate_issuance_config on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Certificate Manager location.

     To set the location attribute:
     + provide the argument certificate_issuance_config on the command
       line with a fully specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Human-readable description of the resource. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update a Certificate Issuance Config called my-cic, run:

    $ gcloud certificate-manager issuance-configs update my-cic \
        --description="updated description" \
        --update-labels=my-key1=my-updated-value1 \
        --remove-labels=my-key2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/issuance-configs/update)

---