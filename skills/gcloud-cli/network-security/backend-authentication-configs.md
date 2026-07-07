# gcloud network-security backend-authentication-configs

manage Network Security BackendAuthenticationConfigs

### `gcloud network-security backend-authentication-configs create`

Create a BackendAuthenticationConfig

Create a new BackendAuthenticationConfig.

**Synopsis:**
```
gcloud network-security backend-authentication-configs create
    (BACKEND_AUTHENTICATION_CONFIG : --location=LOCATION) [--async]
    [--client-certificate=CLIENT_CERTIFICATE] [--description=DESCRIPTION]
    [--labels=[KEY=VALUE,...]] [--trust-config=TRUST_CONFIG]
    [--well-known-roots=WELL_KNOWN_ROOTS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backend authentication config resource - Realm to be created. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument backend_authentication_config on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKEND_AUTHENTICATION_CONFIG
     ID of the backend authentication config or fully qualified identifier
     for the backend authentication config.

     To set the backend_authentication_config attribute:
     + provide the argument backend_authentication_config on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument backend_authentication_config on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--client-certificate` | CLIENT_CERTIFICATE |  | ID of certificate resource. |
| `--description` | DESCRIPTION |  | Description of the backend authentication config. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. |
| `--trust-config` | TRUST_CONFIG |  | ID of trust config resource. |
| `--well-known-roots` | one of: none, public-roots |  | Indicates whether the load balancer should trust backend server certificates. WELL_KNOWN_ROOTS must be one of: none, public-roots. |


**Examples:**
```bash
To create a config named backend-authentication-config, run:

    $ gcloud network-security backend-authentication-configs create \
        backend-authentication-config \
        --trust-config=projects/my-project/locations/global/\
    trustConfigs/my-trust-config --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/backend-authentication-configs/create)

---
### `gcloud network-security backend-authentication-configs delete`

Delete BackendAuthenticationConfig

Delete the specified BackendAuthenticationConfig.

**Synopsis:**
```
gcloud network-security backend-authentication-configs delete
    (BACKEND_AUTHENTICATION_CONFIG : --location=LOCATION) [--async]
    [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backend authentication config resource - Name of the
BackendAuthenticationConfig you want to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument backend_authentication_config on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKEND_AUTHENTICATION_CONFIG
     ID of the backend authentication config or fully qualified identifier
     for the backend authentication config.

     To set the backend_authentication_config attribute:
     + provide the argument backend_authentication_config on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument backend_authentication_config on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | The entity-tag of the BackendAuthenticationConfig. |


**Examples:**
```bash
To delete a BackendAuthenticationConfig called
'my-backend-authentication-config', run:

    $ gcloud network-security backend-authentication-configs delete \
        my-backend-authentication-config --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/backend-authentication-configs/delete)

---
### `gcloud network-security backend-authentication-configs describe`

Describe BackendAuthenticationConfig

Describe the specified BackendAuthenticationConfig.

**Synopsis:**
```
gcloud network-security backend-authentication-configs describe
    (BACKEND_AUTHENTICATION_CONFIG : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backend authentication config resource - The BackendAuthenticationConfig
you want to describe. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backend_authentication_config on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKEND_AUTHENTICATION_CONFIG
     ID of the backend authentication config or fully qualified identifier
     for the backend authentication config.

     To set the backend_authentication_config attribute:
     + provide the argument backend_authentication_config on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument backend_authentication_config on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a BackendAuthenticationConfig called
'my-backend-authentication-config', run:

    $ gcloud network-security backend-authentication-configs describe \
        my-backend-authentication-config --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/backend-authentication-configs/describe)

---
### `gcloud network-security backend-authentication-configs export`

Export BackendAuthenticationConfig

Export a BackendAuthenticationConfig.

**Synopsis:**
```
gcloud network-security backend-authentication-configs export
    (BACKEND_AUTHENTICATION_CONFIG : --location=LOCATION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backend authentication config resource - Name of the
BackendAuthenticationConfig to export. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backend_authentication_config on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKEND_AUTHENTICATION_CONFIG
     ID of the backend authentication config or fully qualified identifier
     for the backend authentication config.

     To set the backend_authentication_config attribute:
     + provide the argument backend_authentication_config on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument backend_authentication_config on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export a BackendAuthenticationConfig, run:

    $ gcloud network-security backend-authentication-configs export \
        my-backend-authentication-config \
        --destination=my-backend-authentication-config.yaml \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/backend-authentication-configs/export)

---
### `gcloud network-security backend-authentication-configs import`

Import BackendAuthenticationConfigs

Import a BackendAuthenticationConfigs.

**Synopsis:**
```
gcloud network-security backend-authentication-configs import
    (BACKEND_AUTHENTICATION_CONFIG : --location=LOCATION) [--async]
    [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backend authentication config resource - Name of the
BackendAuthenticationConfigs to import. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backend_authentication_config on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKEND_AUTHENTICATION_CONFIG
     ID of the backend authentication config or fully qualified identifier
     for the backend authentication config.

     To set the backend_authentication_config attribute:
     + provide the argument backend_authentication_config on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument backend_authentication_config on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Path to a YAML file containing the configuration export data. The YAML file must not contain any output-only fields. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... $CLOUDSDKROOT is can be obtained with the following command: $ gcloud info --format='value(installation.sdk_root)' |


**Examples:**
```bash
To import a BackendAuthenticationConfigs from a YAML file, run:

    $ gcloud network-security backend-authentication-configs import \
        my-backend-authentication-config \
        --source=my-backend-authentication-config.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/backend-authentication-configs/import)

---
### `gcloud network-security backend-authentication-configs list`

List BackendAuthenticationConfigs

List all BackendAuthenticationConfigs in the current project.

**Synopsis:**
```
gcloud network-security backend-authentication-configs list
    [--location=LOCATION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + if left empty, will use the wildcard '-' to list all locations. |


**Examples:**
```bash
To list BackendAuthenticationConfigs in the current project, run:

    $ gcloud network-security backend-authentication-configs list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/backend-authentication-configs/list)

---