# gcloud compute zones

list Compute Engine zones

### `gcloud compute zones describe`

Describe a Compute Engine zone

gcloud compute zones describe displays all data associated with a Compute
Engine zone.

**Synopsis:**
```
gcloud compute zones describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the zone to describe.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/zones/describe)

---
### `gcloud compute zones list`

List Google Compute Engine zones

gcloud compute zones list displays all Google Compute Engine zones in a
project.

**Synopsis:**
```
gcloud compute zones list [NAME ...] [--regexp=REGEXP, -r REGEXP]
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
To list all zones in a project in table form, run:

    $ gcloud compute zones list

To list the URIs of all zones in a project, run:

    $ gcloud compute zones list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/zones/list)

---