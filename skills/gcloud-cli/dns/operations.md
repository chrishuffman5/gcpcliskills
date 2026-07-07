# gcloud dns operations

manage your Cloud DNS operations

### `gcloud dns operations describe`

Describe an operation

This command displays the details of a single managed-zone operation.

**Synopsis:**
```
gcloud dns operations describe OPERATION_ID --zone=ZONE, -z ZONE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION_ID
   The id of the operation to display.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE, -z ZONE |  | Name of zone to get operations from. |


**Examples:**
```bash
To describe a managed-zone operation:

    $ gcloud dns operations describe 1234 --zone=my_zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/operations/describe)

---
### `gcloud dns operations list`

List Cloud DNS operations

This command displays Cloud DNS operations for one or more Cloud DNS
managed-zones (see $ gcloud dns managed-zones --help).

**Synopsis:**
```
gcloud dns operations list --zones=[ZONES,...] [--filter=EXPRESSION]
    [--limit=LIMIT] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zones` | [ZONES,...] |  | _[This must be specified.]_ IDs of the zones or fully qualified identifiers for the zones. To set the zone attribute: + provide the argument --zones on the command line. |


**Examples:**
```bash
To see the list of all operations for two managed-zones, run:

    $ gcloud dns operations list --zones=zone1,zone2

To see the last 5 operations for two managed-zones, run:

    $ gcloud dns operations list --zones=zone1,zone2 \
        --sort-by=~start_time --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/operations/list)

---