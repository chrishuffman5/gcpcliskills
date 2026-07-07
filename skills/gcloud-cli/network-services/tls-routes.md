# gcloud network-services tls-routes

manage Network Services TlsRoutes

### `gcloud network-services tls-routes delete`

Delete tls route

Delete the specified tls route.

**Synopsis:**
```
gcloud network-services tls-routes delete (TLS_ROUTE : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tls route resource - Name of the tls route you want to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument tls_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TLS_ROUTE
     ID of the tls route or fully qualified identifier for the tls route.

     To set the tls_route attribute:
     + provide the argument tls_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument tls_route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a tls route named my-tls-route, run:

    $ gcloud network-services tls-routes delete my-tls-route \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/tls-routes/delete)

---
### `gcloud network-services tls-routes describe`

Describe a tls route

Show details of a tls route.

**Synopsis:**
```
gcloud network-services tls-routes describe
    (TLS_ROUTE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tls route resource - Name of the tls route to be described. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument tls_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TLS_ROUTE
     ID of the tls route or fully qualified identifier for the tls route.

     To set the tls_route attribute:
     + provide the argument tls_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument tls_route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
Show details about a tls route named my-tls-route.

    $ gcloud network-services tls-routes describe my-tls-route \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/tls-routes/describe)

---
### `gcloud network-services tls-routes export`

Export tls route

Export a tls route.

**Synopsis:**
```
gcloud network-services tls-routes export (TLS_ROUTE : --location=LOCATION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tls route resource - Name of the tls route to export. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument tls_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TLS_ROUTE
     ID of the tls route or fully qualified identifier for the tls route.

     To set the tls_route attribute:
     + provide the argument tls_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument tls_route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export a tls route named my-tls-route to a YAML file, run:

    $ gcloud network-services tls-routes export my-tls-route \
        --destination=my-tls-route.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/tls-routes/export)

---
### `gcloud network-services tls-routes import`

Import tls route

Import a tls route.

**Synopsis:**
```
gcloud network-services tls-routes import (TLS_ROUTE : --location=LOCATION)
    [--async] [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tls route resource - Name of the tls route to import. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument tls_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TLS_ROUTE
     ID of the tls route or fully qualified identifier for the tls route.

     To set the tls_route attribute:
     + provide the argument tls_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument tls_route on the command line with a fully
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
To import a tls route named my-tls-route from a YAML file, run:

    $ gcloud network-services tls-routes import my-tls-route \
        --source=my-tls-route.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/tls-routes/import)

---
### `gcloud network-services tls-routes list`

List tls routes

List all tls routes in the specified location of the current project.

**Synopsis:**
```
gcloud network-services tls-routes list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list tls routes in the current project, run:

    $ gcloud network-services tls-routes list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/tls-routes/list)

---