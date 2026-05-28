# gcloud compute regions

list Compute Engine regions

### `gcloud compute regions describe`

Describe a Compute Engine region

gcloud compute regions describe displays all data associated with a Compute
Engine region.

**Synopsis:**
```
gcloud compute regions describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the region to describe.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/regions/describe)

---
### `gcloud compute regions list`

List Google Compute Engine regions

gcloud compute regions list displays all Google Compute Engine regions in a
project.

**Synopsis:**
```
gcloud compute regions list [NAME ...] [--regexp=REGEXP, -r REGEXP]
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
To list all regions in a project in table form, run:

    $ gcloud compute regions list

To list the URIs of all regions in a project, run:

    $ gcloud compute regions list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/regions/list)

---