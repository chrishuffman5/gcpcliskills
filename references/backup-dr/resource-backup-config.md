# gcloud backup-dr resource-backup-config

show protection summary for resources in a particular location and project

### `gcloud backup-dr resource-backup-config list`

Show backup configuration metadata associated with specified resources in a particular location for the project

Show backup configuration metadata associated with specified resources in a
particular location for the project.

**Synopsis:**
```
gcloud backup-dr resource-backup-config list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
  o To list protection summary for a resource named resource-1:

    $ gcloud backup-dr resource-backup-config list \
    --project=sample-project --location=us-central1 \
    --filter="target_resource_display_name=resource-1"

  o To list protection summary for a resource named resource-1 that has
    backup configured:

    $ gcloud backup-dr resource-backup-config list \
    --project=sample-project --location=us-central1 \
    --filter="target_resource_display_name=resource-1 AND \
    backup_configured=true"

You can sort the results using the --sort-by flag. The only supported field
for sorting is target_resource_display_name.

Example of sorting:

    $ gcloud backup-dr resource-backup-config list \
        --project=sample-project --location=us-central1 \
        --sort-by="target_resource_display_name"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/resource-backup-config/list)

---