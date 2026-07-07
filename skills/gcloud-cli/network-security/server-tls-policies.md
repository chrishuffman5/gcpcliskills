# gcloud network-security server-tls-policies

manage Network Security ServerTlsPolicies

### `gcloud network-security server-tls-policies delete`

Delete ServerTlsPolicy

Delete the specified ServerTlsPolicy.

**Synopsis:**
```
gcloud network-security server-tls-policies delete
    (SERVER_TLS_POLICY : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Server TLS policy resource - Name of the ServerTlsPolicy you want to
delete. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument server_tls_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVER_TLS_POLICY
     ID of the server TLS policy or fully qualified identifier for the
     server TLS policy.

     To set the server_tls_policy attribute:
     + provide the argument server_tls_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument server_tls_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a ServerTlsPolicy called 'my-server-tls-policy', run:

    $ gcloud network-security server-tls-policies delete \
        my-server-tls-policy --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/server-tls-policies/delete)

---
### `gcloud network-security server-tls-policies describe`

Describe ServerTlsPolicy

Describe the specified ServerTlsPolicy.

**Synopsis:**
```
gcloud network-security server-tls-policies describe
    (SERVER_TLS_POLICY : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Server TLS policy resource - The ServerTlsPolicy you want to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument server_tls_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVER_TLS_POLICY
     ID of the server TLS policy or fully qualified identifier for the
     server TLS policy.

     To set the server_tls_policy attribute:
     + provide the argument server_tls_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument server_tls_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a ServerTlsPolicy called 'my-server-tls-policy', run:

    $ gcloud network-security server-tls-policies describe \
        my-server-tls-policy --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/server-tls-policies/describe)

---
### `gcloud network-security server-tls-policies export`

Export ServerTlsPolicy

Export a ServerTlsPolicy.

**Synopsis:**
```
gcloud network-security server-tls-policies export
    (SERVER_TLS_POLICY : --location=LOCATION) [--destination=DESTINATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Server TLS policy resource - Name of the ServerTlsPolicy to export. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument server_tls_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVER_TLS_POLICY
     ID of the server TLS policy or fully qualified identifier for the
     server TLS policy.

     To set the server_tls_policy attribute:
     + provide the argument server_tls_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument server_tls_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export a ServerTlsPolicy, run:

    $ gcloud network-security server-tls-policies export \
        my-server-tls-policy --destination=my-server-tls-policy.yaml \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/server-tls-policies/export)

---
### `gcloud network-security server-tls-policies import`

Import ServerTlsPolicy

Import a ServerTlsPolicy.

**Synopsis:**
```
gcloud network-security server-tls-policies import
    (SERVER_TLS_POLICY : --location=LOCATION) [--async] [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Server TLS policy resource - Name of the ServerTlsPolicy to import. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument server_tls_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVER_TLS_POLICY
     ID of the server TLS policy or fully qualified identifier for the
     server TLS policy.

     To set the server_tls_policy attribute:
     + provide the argument server_tls_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument server_tls_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Path to a YAML file containing the configuration export data. The YAML file must not contain any output-only fields. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... $CLOUDSDKROOT is can be obtained with the following command: $ gcloud info --format='value(installation.sdk_root)' |


**Examples:**
```bash
To import a ServerTlsPolicy from a YAML file, run:

    $ gcloud network-security server-tls-policies import \
        my-server-tls-policy --source=my-server-tls-policy.yaml \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/server-tls-policies/import)

---
### `gcloud network-security server-tls-policies list`

List ServerTlsPolicies

List all ServerTlsPolicies in the current project.

**Synopsis:**
```
gcloud network-security server-tls-policies list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + if left empty, will use the wildcard '-' to list all locations. |


**Examples:**
```bash
To list ServerTlsPolicies in the current project, run:

    $ gcloud network-security server-tls-policies list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/server-tls-policies/list)

---