# gcloud compute operations

read and manipulate Compute Engine operations

### `gcloud compute operations describe`

Describe a Compute Engine operation

gcloud compute operations describe displays all data associated with a
Compute Engine operation in a project.

**Synopsis:**
```
gcloud compute operations describe NAME
    [--global | --region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the operation returned by an asynchronous command. Use gcloud
   compute operations list to display recent operations.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the operation is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the operation to describe. Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the operation to describe. Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To get details about a global operation (e.g. operation-111-222-333-444),
run:

    $ gcloud compute operations describe operation-111-222-333-444 \
        --global

To get details about a regional operation, run:

    $ gcloud compute operations describe operation-111-222-333-444 \
        --region=us-central1

To get details about a zonal operation, run:

    $ gcloud compute operations describe operation-111-222-333-444 \
        --zone=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/operations/describe)

---
### `gcloud compute operations list`

List Google Compute Engine operations

gcloud compute operations list displays all Google Compute Engine
operations in a project.

By default, global operations and operations from all regions are listed.
The results can be narrowed down by providing the --global or --regions
flag.

**Synopsis:**
```
gcloud compute operations list [NAME ...] [--regexp=REGEXP, -r REGEXP]
    [--global | --regions=[REGION,...] | --zones=[ZONE,...]]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[NAME ...]
   (DEPRECATED) If provided, show details for the specified names and/or
   URIs of resources.

   Argument NAME is deprecated. Use --filter="name=( 'NAME' ... )"
   instead.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |


**Examples:**
```bash
To list all operations in a project in table form, run:

    $ gcloud compute operations list

To list the URIs of all operations in a project, run:

    $ gcloud compute operations list --uri

To list all global operations in a project, run:

    $ gcloud compute operations list --global

To list all operations in the us-central1 and europe-west1 regions, given
they are regional resources, run:

    $ gcloud compute operations list \
        --filter="region:( europe-west1 us-central1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/operations/list)

---