# gcloud vmware announcements

manage announcements in Google Cloud VMware Engine

### `gcloud vmware announcements list`

List announcements in a Google Cloud VMware Engine

List announcements in a VMware Engine.

**Synopsis:**
```
gcloud vmware announcements list --type=TYPE [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | TYPE |  | The type of announcement to list. TYPE must be (only one value is supported): maintenance. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list maintanance announcements run:

    $ gcloud vmware announcements list --type=maintenance \
        --location=us-west2-a --project=my-project

    Or:

    $ gcloud vmware announcements list --type=maintenance

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/announcements/list)

---