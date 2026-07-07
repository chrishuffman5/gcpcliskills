# gcloud network-services gateways

manage Network Services Gateways

### `gcloud network-services gateways delete`

Delete a gateway

Delete the specified Network Services gateway.

**Synopsis:**
```
gcloud network-services gateways delete (GATEWAY : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Gateway resource - Name of the gateway you want to delete. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument gateway on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GATEWAY
     ID of the gateway or fully qualified identifier for the gateway.

     To set the gateway attribute:
     + provide the argument gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument gateway on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a gateway named 'my-gateway', run:

    $ gcloud network-services gateways delete my-gateway \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/gateways/delete)

---
### `gcloud network-services gateways describe`

Describe a gateway

Show the details of a Network Services gateway.

**Synopsis:**
```
gcloud network-services gateways describe (GATEWAY : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Gateway resource - Name of the gateway to be described. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument gateway on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GATEWAY
     ID of the gateway or fully qualified identifier for the gateway.

     To set the gateway attribute:
     + provide the argument gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument gateway on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
Show details about a gateway named 'my-gateway'.

    $ gcloud network-services gateways describe my-gateway \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/gateways/describe)

---
### `gcloud network-services gateways export`

Export the configuration for a gateway

Export the configuration for a Network Services gateway.

**Synopsis:**
```
gcloud network-services gateways export (GATEWAY : --location=LOCATION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Gateway resource - Name of the gateway to export. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument gateway on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GATEWAY
     ID of the gateway or fully qualified identifier for the gateway.

     To set the gateway attribute:
     + provide the argument gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument gateway on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export a gateway named 'my-gateway' to a YAML file, run:

    $ gcloud network-services gateways export my-gateway \
        --destination=my-gateway.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/gateways/export)

---
### `gcloud network-services gateways import`

Import the configuration for a gateway

Import the configuration for a Network Services gateway.

**Synopsis:**
```
gcloud network-services gateways import (GATEWAY : --location=LOCATION)
    [--async] [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Gateway resource - Name of the gateway to import. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument gateway on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GATEWAY
     ID of the gateway or fully qualified identifier for the gateway.

     To set the gateway attribute:
     + provide the argument gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument gateway on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Path to a YAML file containing the configuration export data. The YAML file must not contain any output-only fields. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... $CLOUDSDKROOT is can be obtained with the following command: $ gcloud info --format='value(installation.sdk_root)' |


**Examples:**
```bash
To import a gateway named 'my-gateway' from a YAML file, run:

    $ gcloud network-services gateways import my-gateway \
        --source=my-gateway.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/gateways/import)

---
### `gcloud network-services gateways list`

List gateways

List all Network Services gateways in the specified location of the current
project.

**Synopsis:**
```
gcloud network-services gateways list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list gateways in the current project, run:

    $ gcloud network-services gateways list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/gateways/list)

---