# gcloud network-services grpc-routes

manage Network Services GrpcRoutes

### `gcloud network-services grpc-routes delete`

Delete grpc route

Delete the specified grpc route.

**Synopsis:**
```
gcloud network-services grpc-routes delete
    (GRPC_ROUTE : --location=LOCATION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Grpc route resource - Name of the grpc route you want to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument grpc_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GRPC_ROUTE
     ID of the grpc route or fully qualified identifier for the grpc
     route.

     To set the grpc_route attribute:
     + provide the argument grpc_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument grpc_route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a grpc route named 'my-grpc-route', run:

    $ gcloud network-services grpc-routes delete my-grpc-route \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/grpc-routes/delete)

---
### `gcloud network-services grpc-routes describe`

Describe a grpc route

Show details of a grpc route.

**Synopsis:**
```
gcloud network-services grpc-routes describe
    (GRPC_ROUTE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Grpc route resource - Name of the grpc route to be described. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument grpc_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GRPC_ROUTE
     ID of the grpc route or fully qualified identifier for the grpc
     route.

     To set the grpc_route attribute:
     + provide the argument grpc_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument grpc_route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
Show details about a grpc route named 'my-grpc-route'.

    $ gcloud network-services grpc-routes describe my-grpc-route \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/grpc-routes/describe)

---
### `gcloud network-services grpc-routes export`

Export grpc route

Export a grpc route.

**Synopsis:**
```
gcloud network-services grpc-routes export
    (GRPC_ROUTE : --location=LOCATION) [--destination=DESTINATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Grpc route resource - Name of the grpc route to export. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument grpc_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GRPC_ROUTE
     ID of the grpc route or fully qualified identifier for the grpc
     route.

     To set the grpc_route attribute:
     + provide the argument grpc_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument grpc_route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export a grpc route named 'my-grpc-route' to a YAML file, run:

    $ gcloud network-services grpc-routes export my-grpc-route \
        --destination=my-grpc-route.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/grpc-routes/export)

---
### `gcloud network-services grpc-routes import`

Import grpc route

Import a grpc route.

**Synopsis:**
```
gcloud network-services grpc-routes import
    (GRPC_ROUTE : --location=LOCATION) [--async] [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Grpc route resource - Name of the grpc route to import. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument grpc_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GRPC_ROUTE
     ID of the grpc route or fully qualified identifier for the grpc
     route.

     To set the grpc_route attribute:
     + provide the argument grpc_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument grpc_route on the command line with a fully
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
To import a grpc route named 'my-grpc-route' from a YAML file, run:

    $ gcloud network-services grpc-routes import my-grpc-route \
        --source=my-grpc-route.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/grpc-routes/import)

---
### `gcloud network-services grpc-routes list`

List grpc routes

List all grpc routes in the specified location of the current project.

**Synopsis:**
```
gcloud network-services grpc-routes list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list grpc routes in the current project, run:

    $ gcloud network-services grpc-routes list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/grpc-routes/list)

---