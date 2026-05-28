# gcloud network-security tls-inspection-policies

manage Network Security TLS Inspection Policies

### `gcloud network-security tls-inspection-policies delete`

Delete TLS Inspection Policy

Delete the specified TLS Inspection Policy.

**Synopsis:**
```
gcloud network-security tls-inspection-policies delete
    (TLS_INSPECTION_POLICY : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tls inspection policy resource - Name of the TLS Inspection Policy you
want to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument tls_inspection_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TLS_INSPECTION_POLICY
     ID of the tls inspection policy or fully qualified identifier for the
     tls inspection policy.

     To set the tls_inspection_policy attribute:
     + provide the argument tls_inspection_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument tls_inspection_policy on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a TLS Inspection Policy called 'my-tls-inspection-policy', run:

    $ gcloud network-security tls-inspection-policies delete \
        my-tls-inspection-policy --location=$REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/tls-inspection-policies/delete)

---
### `gcloud network-security tls-inspection-policies export`

Export TLS Inspection Policy

Export a TLS Inspection Policy.

**Synopsis:**
```
gcloud network-security tls-inspection-policies export
    (TLS_INSPECTION_POLICY : --location=LOCATION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tls inspection policy resource - The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument tls_inspection_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TLS_INSPECTION_POLICY
     ID of the tls inspection policy or fully qualified identifier for the
     tls inspection policy.

     To set the tls_inspection_policy attribute:
     + provide the argument tls_inspection_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument tls_inspection_policy on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export a TLS Inspection Policy, run:

    $ gcloud network-security tls-inspection-policies export \
        my-tls-inspection-policy \
        --destination=my-tls-inspection-policy.yaml --location=$REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/tls-inspection-policies/export)

---
### `gcloud network-security tls-inspection-policies import`

Import TLS Inspection Policy

Import a TLS Inspection Policy.

**Synopsis:**
```
gcloud network-security tls-inspection-policies import
    (TLS_INSPECTION_POLICY : --location=LOCATION) [--async]
    [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tls inspection policy resource - Name of the TLS Inspection Policy to
import. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument tls_inspection_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TLS_INSPECTION_POLICY
     ID of the tls inspection policy or fully qualified identifier for the
     tls inspection policy.

     To set the tls_inspection_policy attribute:
     + provide the argument tls_inspection_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument tls_inspection_policy on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Path to a YAML file containing the configuration export data. The YAML file must not contain any output-only fields. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... $CLOUDSDKROOT is can be obtained with the following command: $ gcloud info --format='value(installation.sdk_root)' |


**Examples:**
```bash
To import a TLS Inspection Policy from a YAML file, run:        $ gcloud network-security tls-inspection-policies import \
        my-tls-inspection-policy \
        --source=my-tls-inspection-policy.yaml --location=$REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/tls-inspection-policies/import)

---
### `gcloud network-security tls-inspection-policies list`

List TLS Inspection Policies

List all TLS Inspection Policies in the specified location of the current
project.

**Synopsis:**
```
gcloud network-security tls-inspection-policies list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list TLS Inspection Policies in the current project, run:        $ gcloud network-security tls-inspection-policies list \
        --location=$REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/tls-inspection-policies/list)

---