# gcloud compute disk-types

read Compute Engine virtual disk types

### `gcloud compute disk-types describe`

Describe a Compute Engine disk type

gcloud compute disk-types describe displays all data associated with a
Compute Engine disk type.

**Synopsis:**
```
gcloud compute disk-types describe DISK_TYPE [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_TYPE
   Name of the disk type to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the disk type to describe. Overrides the default compute/zone property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disk-types/describe)

---
### `gcloud compute disk-types list`

List Google Compute Engine disk types

gcloud compute disk-types list displays all Google Compute Engine disk
types in a project.

By default, disk types from all zones are listed. The results can be
narrowed down using a filter: --filter="zone:( ZONE ... )".

**Synopsis:**
```
gcloud compute disk-types list [NAME ...] [--regexp=REGEXP, -r REGEXP]
    [--zones=ZONE,[ZONE,...]] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
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
| `--zones` | ZONE,[ZONE,...] |  | If provided, only resources from the given zones are queried. |


**Examples:**
```bash
To list all disk types in a project in table form, run:

    $ gcloud compute disk-types list

To list the URIs of all disk types in a project, run:

    $ gcloud compute disk-types list --uri

To list all disk types in the us-central1-b and europe-west1-d zones, run:

    $ gcloud compute disk-types list \
        --filter="zone:( us-central1-b europe-west1-d )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disk-types/list)

---