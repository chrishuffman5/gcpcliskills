# gcloud datastream routes

manage Datastream routes

### `gcloud datastream routes create`

Create a Datastream private connection route

**Synopsis:**
```
gcloud datastream routes create
    (ROUTE : --location=LOCATION --private-connection=PRIVATE_CONNECTION)
    --destination-address=DESTINATION_ADDRESS --display-name=DISPLAY_NAME
    [--destination-port=DESTINATION_PORT] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Route resource - The route to create. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument route on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROUTE
     ID of the route or fully qualified identifier for the route.

     To set the route attribute:
     + provide the argument route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the route.

     To set the location attribute:
     + provide the argument route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --private-connection=PRIVATE_CONNECTION
     The private connection of the route.

     To set the private-connection attribute:
     + provide the argument route on the command line with a fully
       specified name;
     + provide the argument --private-connection on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-address` | DESTINATION_ADDRESS |  | Destination address for connection. |
| `--display-name` | DISPLAY_NAME |  | Friendly name for the route. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-port` | DESTINATION_PORT |  | Destination port for connection. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a route called 'my-route', run:

    $ gcloud datastream routes create my-route --location=us-central1 \
      --private-connection=private-connection \
      --display-name=my-display-name \
      --destination-address=addr.path.to.somewhere \
      --destination-port=33665
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/routes/create)

---
### `gcloud datastream routes delete`

Delete a Datastream private connection route

Deletes a Datastream private connection route.

**Synopsis:**
```
gcloud datastream routes delete
    (ROUTE : --location=LOCATION --private-connection=PRIVATE_CONNECTION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Route resource - The Route to delete. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument route on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROUTE
     ID of the route or fully qualified identifier for the route.

     To set the route attribute:
     + provide the argument route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resources.

     To set the location attribute:
     + provide the argument route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --private-connection=PRIVATE_CONNECTION
     The private connection name.

     To set the private-connection attribute:
     + provide the argument route on the command line with a fully
       specified name;
     + provide the argument --private-connection on the command line.
```

**Examples:**
```bash
To delete a Datastream private connection route:

    $ gcloud datastream routes delete ROUTE --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/routes/delete)

---
### `gcloud datastream routes describe`

Show details about the route

Show details about the route.

**Synopsis:**
```
gcloud datastream routes describe
    (ROUTE : --location=LOCATION --private-connection=PRIVATE_CONNECTION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Route resource - The route you want to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument route on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROUTE
     ID of the route or fully qualified identifier for the route.

     To set the route attribute:
     + provide the argument route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resources.

     To set the location attribute:
     + provide the argument route on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --private-connection=PRIVATE_CONNECTION
     The private connection name.

     To set the private-connection attribute:
     + provide the argument route on the command line with a fully
       specified name;
     + provide the argument --private-connection on the command line.
```

**Examples:**
```bash
To show details about a device, run:

    $ gcloud datastream routes describe my-route \
        --private-connection=pc --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/routes/describe)

---
### `gcloud datastream routes list`

List Datastream routes

List Datastream routes.

**Synopsis:**
```
gcloud datastream routes list
    (--private-connection=PRIVATE_CONNECTION : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-connection` | PRIVATE_CONNECTION |  | _[This must be specified.]_ ID of the private_connection or fully qualified identifier for the private_connection. To set the private-connection attribute: + provide the argument --private-connection on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location of the resources. To set the location attribute: + provide the argument --private-connection on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list the routes, run:

    $ gcloud datastream routes list --private-connection=pc \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/routes/list)

---