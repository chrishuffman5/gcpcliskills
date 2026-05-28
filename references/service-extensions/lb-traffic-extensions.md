# gcloud service-extensions lb-traffic-extensions

manage Service Extensions LbTrafficExtension resources

### `gcloud service-extensions lb-traffic-extensions delete`

Delete an LbTrafficExtension resource

Delete the specified LbTrafficExtension resource.

**Synopsis:**
```
gcloud service-extensions lb-traffic-extensions delete
    (LB_TRAFFIC_EXTENSION : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LbTrafficExtension resource - The ID of the deleted LbTrafficExtension
resource. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument lb_traffic_extension on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LB_TRAFFIC_EXTENSION
     ID of the LbTrafficExtension or fully qualified identifier for the
     LbTrafficExtension.

     To set the lb_traffic_extension attribute:
     + provide the argument lb_traffic_extension on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud region in which the resource is located.

     To set the location attribute:
     + provide the argument lb_traffic_extension on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an LbTrafficExtension resource named my-traffic-extension in
us-central1, run:

    $ gcloud service-extensions lb-traffic-extensions delete \
        my-traffic-extension --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/lb-traffic-extensions/delete)

---
### `gcloud service-extensions lb-traffic-extensions describe`

Describe an LbTrafficExtension resource

Show details of an LbTrafficExtension resource.

**Synopsis:**
```
gcloud service-extensions lb-traffic-extensions describe
    (LB_TRAFFIC_EXTENSION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LbTrafficExtension resource - The ID of the LbTrafficExtension resource.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument lb_traffic_extension on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LB_TRAFFIC_EXTENSION
     ID of the LbTrafficExtension or fully qualified identifier for the
     LbTrafficExtension.

     To set the lb_traffic_extension attribute:
     + provide the argument lb_traffic_extension on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud region in which the resource is located.

     To set the location attribute:
     + provide the argument lb_traffic_extension on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To show details about the LbTrafficExtension resource named
my-traffic-extension located in us-central1.

    $ gcloud service-extensions lb-traffic-extensions describe \
        my-traffic-extension --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/lb-traffic-extensions/describe)

---
### `gcloud service-extensions lb-traffic-extensions import`

Import an LbTrafficExtension resource

Import an LbTrafficExtension resource defined in a YAML file.

**Synopsis:**
```
gcloud service-extensions lb-traffic-extensions import
    (LB_TRAFFIC_EXTENSION : --location=LOCATION) [--async]
    [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LbTrafficExtension resource - The ID of the new or updated
LbTrafficExtension resource. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument lb_traffic_extension on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LB_TRAFFIC_EXTENSION
     ID of the LbTrafficExtension or fully qualified identifier for the
     LbTrafficExtension.

     To set the lb_traffic_extension attribute:
     + provide the argument lb_traffic_extension on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud region in which the resource is located.

     To set the location attribute:
     + provide the argument lb_traffic_extension on the command line
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
To import an LbTrafficExtension resource named my-traffic-extension from a
YAML file in us-central1, run:

    $ gcloud service-extensions lb-traffic-extensions import \
      my-traffic-extension --source=my-traffic-extension.yaml \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/lb-traffic-extensions/import)

---
### `gcloud service-extensions lb-traffic-extensions list`

List LbTrafficExtension resources

List all LbTrafficExtension resources in the specified location of the
current project.

**Synopsis:**
```
gcloud service-extensions lb-traffic-extensions list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all LbTrafficExtension resources in the current project located in
us-central1 region, run:

    $ gcloud service-extensions lb-traffic-extensions list \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/lb-traffic-extensions/list)

---