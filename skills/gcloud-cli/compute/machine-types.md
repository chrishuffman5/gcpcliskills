# gcloud compute machine-types

read Compute Engine virtual machine types

### `gcloud compute machine-types describe`

Describe a Compute Engine machine type

gcloud compute machine-types describe displays all data associated with a
Compute Engine machine type.

**Synopsis:**
```
gcloud compute machine-types describe NAME [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the machine type to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the machine type to describe. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To describe a machine type 'MACHINE-TYPE' in zone 'us-central1-f', run:

    $ gcloud compute machine-types describe MACHINE-TYPE \
        --zone=us-central1-f
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/machine-types/describe)

---
### `gcloud compute machine-types list`

List Google Compute Engine machine types

gcloud compute machine-types list displays all Google Compute Engine
machine types in a project.

By default, machine types from all zones are listed. The results can be
narrowed down using a filter: --filter="zone:( ZONE ... )".

OBSOLETE machine types are filtered out by default. Add --verbosity=info to
display the default filter expression. Use --filter="" to list all images,
or specify your own --filter to override the default.

**Synopsis:**
```
gcloud compute machine-types list [NAME ...] [--regexp=REGEXP, -r REGEXP]
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
To list all machine types in a project in table form, run:

    $ gcloud compute machine-types list

To list the URIs of all machine types in a project, run:

    $ gcloud compute machine-types list --uri

To list all machine types in the us-central1-b and europe-west1-d zones,
run:

    $ gcloud compute machine-types list \
        --filter="zone:( us-central1-b europe-west1-d )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/machine-types/list)

---