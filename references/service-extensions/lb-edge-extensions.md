# gcloud service-extensions lb-edge-extensions

manage Service Extensions LbEdgeExtension resources

### `gcloud service-extensions lb-edge-extensions delete`

Delete an LbEdgeExtension resource

Delete the specified LbEdgeExtension resource.

**Synopsis:**
```
gcloud service-extensions lb-edge-extensions delete
    (LB_EDGE_EXTENSION : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LbEdgeExtension resource - The ID of the deleted LbEdgeExtension resource.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument lb_edge_extension on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LB_EDGE_EXTENSION
     ID of the LbEdgeExtension or fully qualified identifier for the
     LbEdgeExtension.

     To set the lb_edge_extension attribute:
     + provide the argument lb_edge_extension on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud region in which the resource is located.

     To set the location attribute:
     + provide the argument lb_edge_extension on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a global LbEdgeExtension resource named my-edge-extension, run:

    $ gcloud service-extensions lb-edge-extensions delete \
        my-edge-extension --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/lb-edge-extensions/delete)

---
### `gcloud service-extensions lb-edge-extensions describe`

Describe an LbEdgeExtension resource

Show details about an LbEdgeExtension resource.

**Synopsis:**
```
gcloud service-extensions lb-edge-extensions describe
    (LB_EDGE_EXTENSION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LbEdgeExtension resource - The ID of the LbEdgeExtension resource. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument lb_edge_extension on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LB_EDGE_EXTENSION
     ID of the LbEdgeExtension or fully qualified identifier for the
     LbEdgeExtension.

     To set the lb_edge_extension attribute:
     + provide the argument lb_edge_extension on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud region in which the resource is located.

     To set the location attribute:
     + provide the argument lb_edge_extension on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To show details about the global LbEdgeExtension resource named
my-edge-extension.

    $ gcloud service-extensions lb-edge-extensions describe \
        my-edge-extension --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/lb-edge-extensions/describe)

---
### `gcloud service-extensions lb-edge-extensions import`

Import an LbEdgeExtension resource

Import an LbEdgeExtension resource defined in a YAML file.

**Synopsis:**
```
gcloud service-extensions lb-edge-extensions import
    (LB_EDGE_EXTENSION : --location=LOCATION) [--async] [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LbEdgeExtension resource - The ID of the new or updated LbEdgeExtension
resource. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument lb_edge_extension on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LB_EDGE_EXTENSION
     ID of the LbEdgeExtension or fully qualified identifier for the
     LbEdgeExtension.

     To set the lb_edge_extension attribute:
     + provide the argument lb_edge_extension on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud region in which the resource is located.

     To set the location attribute:
     + provide the argument lb_edge_extension on the command line with a
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
To import a global LbEdgeExtension resource named my-edge-extension from a
YAML file, run:

    $ gcloud service-extensions lb-edge-extensions import \
      my-edge-extension --source=my-edge-extension.yaml \
      --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/lb-edge-extensions/import)

---
### `gcloud service-extensions lb-edge-extensions list`

List LbEdgeExtension resources

List all LbEdgeExtension resources in the specified location of the current
project.

**Synopsis:**
```
gcloud service-extensions lb-edge-extensions list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all global LbEdgeExtension resources in the current project, run:

    $ gcloud service-extensions lb-edge-extensions list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/lb-edge-extensions/list)

---