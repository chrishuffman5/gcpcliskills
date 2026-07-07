# gcloud network-services tcp-routes

manage Network Services TcpRoutes

### `gcloud network-services tcp-routes delete`

Delete tcp route

Delete the specified tcp route.

**Synopsis:**
```
gcloud network-services tcp-routes delete (TCP_ROUTE : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tcp route resource - Name of the tcp route you want to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument tcp_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TCP_ROUTE
     ID of the tcp route or fully qualified identifier for the tcp route.

     To set the tcp_route attribute:
     + provide the argument tcp_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument tcp_route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a tcp route named 'my-tcp-route', run:

    $ gcloud network-services tcp-routes delete my-tcp-route \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/tcp-routes/delete)

---
### `gcloud network-services tcp-routes describe`

Describe a TCP route

Show details of a TCP route.

**Synopsis:**
```
gcloud network-services tcp-routes describe
    (TCP_ROUTE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tcp route resource - Name of the TCP route to be described. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument tcp_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TCP_ROUTE
     ID of the tcp route or fully qualified identifier for the tcp route.

     To set the tcp_route attribute:
     + provide the argument tcp_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument tcp_route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
Show details about a TCP route named 'my-tcp-route'.

    $ gcloud network-services tcp-routes describe my-tcp-route \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/tcp-routes/describe)

---
### `gcloud network-services tcp-routes export`

Export tcp route

Export a tcp route.

**Synopsis:**
```
gcloud network-services tcp-routes export (TCP_ROUTE : --location=LOCATION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tcp route resource - Name of the tcp route to export. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument tcp_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TCP_ROUTE
     ID of the tcp route or fully qualified identifier for the tcp route.

     To set the tcp_route attribute:
     + provide the argument tcp_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument tcp_route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export a tcp route named 'my-tcp-route' to a YAML file, run:

    $ gcloud network-services tcp-routes export my-tcp-route \
        --destination=my-tcp-route.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/tcp-routes/export)

---
### `gcloud network-services tcp-routes import`

Import tcp route

Import a tcp route.

**Synopsis:**
```
gcloud network-services tcp-routes import (TCP_ROUTE : --location=LOCATION)
    [--async] [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tcp route resource - Name of the tcp route to import. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument tcp_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TCP_ROUTE
     ID of the tcp route or fully qualified identifier for the tcp route.

     To set the tcp_route attribute:
     + provide the argument tcp_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument tcp_route on the command line with a fully
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
To import a tcp route named 'my-tcp-route' from a YAML file, run:

    $ gcloud network-services tcp-routes import my-tcp-route \
        --source=my-tcp-route.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/tcp-routes/import)

---
### `gcloud network-services tcp-routes list`

List tcp routes

List all tcp routes in the specified location of the current project.

**Synopsis:**
```
gcloud network-services tcp-routes list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list tcp routes in the current project, run:

    $ gcloud network-services tcp-routes list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/tcp-routes/list)

---