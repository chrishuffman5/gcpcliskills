# gcloud compute accelerator-types

read Compute Engine accelerator types

### `gcloud compute accelerator-types describe`

Describe Compute Engine accelerator types

gcloud compute accelerator-types describe displays all data associated with
a Compute Engine accelerator type.

**Synopsis:**
```
gcloud compute accelerator-types describe NAME [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the accelerator type to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the accelerator type to describe. Overrides the default compute/zone property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/accelerator-types/describe)

---
### `gcloud compute accelerator-types list`

List Google Compute Engine accelerator types

gcloud compute accelerator-types list displays all Google Compute Engine
accelerator types in a project.

By default, accelerator types from all zones are listed. The results can be
narrowed down using a filter: --filter="zone:( ZONE ... )".

**Synopsis:**
```
gcloud compute accelerator-types list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all accelerator types in a project in table form, run:

    $ gcloud compute accelerator-types list

To list the URIs of all accelerator types in a project, run:

    $ gcloud compute accelerator-types list --uri

To list all accelerator types in the us-central1-b and europe-west1-d
zones, run:

    $ gcloud compute accelerator-types list \
        --filter="zone:( us-central1-b europe-west1-d )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/accelerator-types/list)

---