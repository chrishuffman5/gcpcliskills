# gcloud network-security client-tls-policies

manage Network Security ClientTlsPolicies

### `gcloud network-security client-tls-policies delete`

Delete ClientTlsPolicy

Delete the specified ClientTlsPolicy.

**Synopsis:**
```
gcloud network-security client-tls-policies delete
    (CLIENT_TLS_POLICY : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Client TLS policy resource - Name of the ClientTlsPolicy you want to
delete. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument client_tls_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLIENT_TLS_POLICY
     ID of the client TLS policy or fully qualified identifier for the
     client TLS policy.

     To set the client_tls_policy attribute:
     + provide the argument client_tls_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument client_tls_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a ClientTlsPolicy called 'my-client-tls-policy', run:

    $ gcloud network-security client-tls-policies delete \
        my-client-tls-policy --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/client-tls-policies/delete)

---
### `gcloud network-security client-tls-policies export`

Export ClientTlsPolicy

Export a ClientTlsPolicy.

**Synopsis:**
```
gcloud network-security client-tls-policies export
    (CLIENT_TLS_POLICY : --location=LOCATION) [--destination=DESTINATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Client TLS policy resource - Name of the ClientTlsPolicy to export. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument client_tls_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLIENT_TLS_POLICY
     ID of the client TLS policy or fully qualified identifier for the
     client TLS policy.

     To set the client_tls_policy attribute:
     + provide the argument client_tls_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument client_tls_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export a ClientTlsPolicy, run:

    $ gcloud network-security client-tls-policies export \
        my-client-tls-policy --destination=my-client-tls-policy.yaml \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/client-tls-policies/export)

---
### `gcloud network-security client-tls-policies import`

Import ClientTlsPolicy

Import a ClientTlsPolicy.

**Synopsis:**
```
gcloud network-security client-tls-policies import
    (CLIENT_TLS_POLICY : --location=LOCATION) [--async] [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Client TLS policy resource - Name of the ClientTlsPolicy to import. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument client_tls_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLIENT_TLS_POLICY
     ID of the client TLS policy or fully qualified identifier for the
     client TLS policy.

     To set the client_tls_policy attribute:
     + provide the argument client_tls_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument client_tls_policy on the command line with a
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
To import a ClientTlsPolicy from a YAML file, run:

    $ gcloud network-security client-tls-policies import \
        my-client-tls-policy --source=my-client-tls-policy.yaml \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/client-tls-policies/import)

---
### `gcloud network-security client-tls-policies list`

List ClientTlsPolicies

List all ClientTlsPolicies in the specified location of the current
project.

**Synopsis:**
```
gcloud network-security client-tls-policies list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list ClientTlsPolicies in the current project, run:

    $ gcloud network-security client-tls-policies list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/client-tls-policies/list)

---