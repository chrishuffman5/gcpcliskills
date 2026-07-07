# gcloud network-services http-routes

manage Network Services HttpRoutes

### `gcloud network-services http-routes delete`

Delete http route

Delete the specified http route.

**Synopsis:**
```
gcloud network-services http-routes delete
    (HTTP_ROUTE : --location=LOCATION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Http route resource - Name of the http route you want to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument http_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HTTP_ROUTE
     ID of the http route or fully qualified identifier for the http
     route.

     To set the http_route attribute:
     + provide the argument http_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument http_route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a route named 'my-route', run:

    $ gcloud network-services http-routes delete my-route \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/http-routes/delete)

---
### `gcloud network-services http-routes describe`

Describe a HTTP route

Show details of a HTTP route.

**Synopsis:**
```
gcloud network-services http-routes describe
    (HTTP_ROUTE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Http route resource - Name of the HTTP route to be described. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument http_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HTTP_ROUTE
     ID of the http route or fully qualified identifier for the http
     route.

     To set the http_route attribute:
     + provide the argument http_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument http_route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
Show details about a HTTP route named 'my-http-route'.

    $ gcloud network-services http-routes describe my-http-route \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/http-routes/describe)

---
### `gcloud network-services http-routes export`

Export http route

Export a http route.

**Synopsis:**
```
gcloud network-services http-routes export
    (HTTP_ROUTE : --location=LOCATION) [--destination=DESTINATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Http route resource - Name of the http route to export. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument http_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HTTP_ROUTE
     ID of the http route or fully qualified identifier for the http
     route.

     To set the http_route attribute:
     + provide the argument http_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument http_route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export a route named 'my-route' to a YAML file, run:

    $ gcloud network-services http-routes export my-route \
        --destination=my-route.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/http-routes/export)

---
### `gcloud network-services http-routes import`

Import http route

Import a http route.

**Synopsis:**
```
gcloud network-services http-routes import
    (HTTP_ROUTE : --location=LOCATION) [--async] [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Http route resource - Name of the http route to import. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument http_route on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HTTP_ROUTE
     ID of the http route or fully qualified identifier for the http
     route.

     To set the http_route attribute:
     + provide the argument http_route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument http_route on the command line with a fully
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
To import a route named 'my-route' from a YAML file, run:

    $ gcloud network-services http-routes import my-route \
        --source=my-route.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/http-routes/import)

---
### `gcloud network-services http-routes list`

List http routes

List all http routes in the specified location of the current project.

**Synopsis:**
```
gcloud network-services http-routes list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list meshes in the current project, run:

    $ gcloud network-services http-routes list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/http-routes/list)

---