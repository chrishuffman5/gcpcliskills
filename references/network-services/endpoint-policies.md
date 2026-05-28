# gcloud network-services endpoint-policies

manage Network Services EndpointPolicies

### `gcloud network-services endpoint-policies delete`

Delete endpoint policy

Delete the specified endpoint policy.

**Synopsis:**
```
gcloud network-services endpoint-policies delete
    (ENDPOINT_POLICY : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint policy resource - Name of the endpoint policy you want to delete.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument endpoint_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT_POLICY
     ID of the endpoint policy or fully qualified identifier for the
     endpoint policy.

     To set the endpoint_policy attribute:
     + provide the argument endpoint_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument endpoint_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an endpoint policy called 'my-endpoint-policy', run:

    $ gcloud network-services endpoint-policies delete \
        my-endpoint-policy --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/endpoint-policies/delete)

---
### `gcloud network-services endpoint-policies describe`

Describe an endpoint policy

Show details of an endpoint policy.

**Synopsis:**
```
gcloud network-services endpoint-policies describe
    (ENDPOINT_POLICY : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint policy resource - Name of the endpoint policy to be described.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument endpoint_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT_POLICY
     ID of the endpoint policy or fully qualified identifier for the
     endpoint policy.

     To set the endpoint_policy attribute:
     + provide the argument endpoint_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument endpoint_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
Show details about an endpointPolicy named 'my-endpoint-policy'.

    $ gcloud network-services endpoint-policies describe \
        my-endpoint-policy --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/endpoint-policies/describe)

---
### `gcloud network-services endpoint-policies export`

Export endpoint policy

Export an endpoit policy.

**Synopsis:**
```
gcloud network-services endpoint-policies export
    (ENDPOINT_POLICY : --location=LOCATION) [--destination=DESTINATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint policy resource - Name of the endpoint policy to export. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument endpoint_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT_POLICY
     ID of the endpoint policy or fully qualified identifier for the
     endpoint policy.

     To set the endpoint_policy attribute:
     + provide the argument endpoint_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument endpoint_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export an endpoint policy named 'my-endpoint-policy', run:

    $ gcloud network-services endpoint-policies export \
        my-endpoint-policy --destination=my-endpoint-policy.yaml \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/endpoint-policies/export)

---
### `gcloud network-services endpoint-policies import`

Import endpoint policy

Import an endpoint policy.

**Synopsis:**
```
gcloud network-services endpoint-policies import
    (ENDPOINT_POLICY : --location=LOCATION) [--async] [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint policy resource - Name of the endpoint policy to import. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument endpoint_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT_POLICY
     ID of the endpoint policy or fully qualified identifier for the
     endpoint policy.

     To set the endpoint_policy attribute:
     + provide the argument endpoint_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument endpoint_policy on the command line with a
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
To import an endpoint policy named 'my-endpoint-policy' from a YAML file,
run:

    $ gcloud network-services endpoint-policies import \
        my-endpoint-policy --source=my-endpoint-policy.yaml \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/endpoint-policies/import)

---
### `gcloud network-services endpoint-policies list`

List endpoint policies

List all endpoint policies in the specified location of the current
project.

**Synopsis:**
```
gcloud network-services endpoint-policies list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list endpoint policies in the current project, run:

    $ gcloud network-services endpoint-policies list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/endpoint-policies/list)

---