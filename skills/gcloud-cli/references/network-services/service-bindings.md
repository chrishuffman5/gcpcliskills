# gcloud network-services service-bindings

manage Network Services Bindings

### `gcloud network-services service-bindings create`

Create a service binding

Create a new service binding with the given name.

**Synopsis:**
```
gcloud network-services service-bindings create
    (SERVICE_BINDING : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service binding resource - Name of the service binding to be created. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service_binding on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_BINDING
     ID of the service binding or fully qualified identifier for the
     service binding.

     To set the service_binding attribute:
     + provide the argument service_binding on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the service binding. |


**Examples:**
```bash
Create a service binding with the name 'my-service-binding' and location
'global'.

    $ gcloud network-services service-bindings create \
        my-service-binding --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/service-bindings/create)

---
### `gcloud network-services service-bindings delete`

Delete service binding

Delete the specified service binding.

**Synopsis:**
```
gcloud network-services service-bindings delete
    (SERVICE_BINDING : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service binding resource - Name of the service binding you want to delete.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service_binding on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_BINDING
     ID of the service binding or fully qualified identifier for the
     service binding.

     To set the service_binding attribute:
     + provide the argument service_binding on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a service binding called 'my-service-binding', run:

    $ gcloud network-services service-bindings delete \
        my-service-binding --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/service-bindings/delete)

---
### `gcloud network-services service-bindings describe`

Describe a service binding

Show details of a service binding.

**Synopsis:**
```
gcloud network-services service-bindings describe
    (SERVICE_BINDING : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service binding resource - Name of the service binding to be described.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service_binding on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_BINDING
     ID of the service binding or fully qualified identifier for the
     service binding.

     To set the service_binding attribute:
     + provide the argument service_binding on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
Show details about a service binding named 'my-service-binding'.

    $ gcloud network-services service-bindings describe \
        my-service-binding --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/service-bindings/describe)

---
### `gcloud network-services service-bindings export`

Export a service binding

Export a service binding to a YAML file.

**Synopsis:**
```
gcloud network-services service-bindings export
    (SERVICE_BINDING : --location=LOCATION) [--destination=DESTINATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service binding resource - Name of the service binding to export. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service_binding on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_BINDING
     ID of the service binding or fully qualified identifier for the
     service binding.

     To set the service_binding attribute:
     + provide the argument service_binding on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export a service binding named 'my-service-binding' to a YAML file, run:

    $ gcloud network-services service-bindings export \
        my-service-binding --destination=my-service-binding.yaml \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/service-bindings/export)

---
### `gcloud network-services service-bindings import`

Import a service binding

Import a service binding from a YAML file.

**Synopsis:**
```
gcloud network-services service-bindings import
    (SERVICE_BINDING : --location=LOCATION) [--async] [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service binding resource - Name of the service binding to import. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service_binding on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_BINDING
     ID of the service binding or fully qualified identifier for the
     service binding.

     To set the service_binding attribute:
     + provide the argument service_binding on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service_binding on the command line with a
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
To import a service binding named my-service-binding from a YAML file, run:

    $ gcloud network-services service-bindings import \
        my-service-binding --source=my-service-binding.yaml \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/service-bindings/import)

---
### `gcloud network-services service-bindings list`

List service bindings

List all service bindings in the specified location of the current project.

**Synopsis:**
```
gcloud network-services service-bindings list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all the global service bindings in the current project, run:

    $ gcloud network-services service-bindings list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/service-bindings/list)

---
### `gcloud network-services service-bindings update`

Update a service binding

Update a service binding with the given name.

**Synopsis:**
```
gcloud network-services service-bindings update
    (SERVICE_BINDING : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service binding resource - Name of the service binding to be updated. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service_binding on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_BINDING
     ID of the service binding or fully qualified identifier for the
     service binding.

     To set the service_binding attribute:
     + provide the argument service_binding on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service_binding on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the service binding. |


**Examples:**
```bash
Update a service binding with the name 'my-service-binding' and location
'global'.

    $ gcloud network-services service-bindings update \
        my-service-binding --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/service-bindings/update)

---