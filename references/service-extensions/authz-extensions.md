# gcloud service-extensions authz-extensions

manage Service Extensions AuthzExtension resources

### `gcloud service-extensions authz-extensions delete`

Delete an AuthzExtension resource

Delete the specified AuthzExtension resource.

**Synopsis:**
```
gcloud service-extensions authz-extensions delete
    (AUTHZ_EXTENSION : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AuthzExtension resource - The ID of the deleted AuthzExtension resource.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument authz_extension on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHZ_EXTENSION
     ID of the AuthzExtension or fully qualified identifier for the
     AuthzExtension.

     To set the authz_extension attribute:
     + provide the argument authz_extension on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud region in which the resource is located.

     To set the location attribute:
     + provide the argument authz_extension on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an AuthzExtension resource named my-authz-extension in
us-central1, run:

    $ gcloud service-extensions authz-extensions delete \
        my-authz-extension --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/authz-extensions/delete)

---
### `gcloud service-extensions authz-extensions describe`

Describe an AuthzExtension resource

Show details about an AuthzExtension resource.

**Synopsis:**
```
gcloud service-extensions authz-extensions describe
    (AUTHZ_EXTENSION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AuthzExtension resource - The ID of the AuthzExtension resource. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument authz_extension on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHZ_EXTENSION
     ID of the AuthzExtension or fully qualified identifier for the
     AuthzExtension.

     To set the authz_extension attribute:
     + provide the argument authz_extension on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud region in which the resource is located.

     To set the location attribute:
     + provide the argument authz_extension on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To show details about the AuthzExtension resource named my-authz-extension
located in us-central1.

    $ gcloud service-extensions authz-extensions describe \
        my-authz-extension --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/authz-extensions/describe)

---
### `gcloud service-extensions authz-extensions import`

Import an AuthzExtension resource

Import an AuthzExtension resource defined in a YAML file.

**Synopsis:**
```
gcloud service-extensions authz-extensions import
    (AUTHZ_EXTENSION : --location=LOCATION) [--async] [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AuthzExtension resource - The ID of the new or updated AuthzExtension
resource. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument authz_extension on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHZ_EXTENSION
     ID of the AuthzExtension or fully qualified identifier for the
     AuthzExtension.

     To set the authz_extension attribute:
     + provide the argument authz_extension on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud region in which the resource is located.

     To set the location attribute:
     + provide the argument authz_extension on the command line with a
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
To import an AuthzExtension resource named my-authz-extension from a YAML
file in us-central1, run:

    $ gcloud service-extensions authz-extensions import \
      my-authz-extension --source=my-authz-extension.yaml \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/authz-extensions/import)

---
### `gcloud service-extensions authz-extensions list`

List AuthzExtension resources

List all AuthzExtension resources in the specified location of the current
project.

**Synopsis:**
```
gcloud service-extensions authz-extensions list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all AuthzExtension resources in the current project located in
us-central1 region run:

    $ gcloud service-extensions authz-extensions list \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions/authz-extensions/list)

---