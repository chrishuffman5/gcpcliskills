# gcloud compute project-zonal-metadata

describe and update project zonal metadata

### `gcloud compute project-zonal-metadata add`

Add or update project zonal metadata

gcloud compute project-zonal-metadata add is used to add or update project
zonal metadata for your VM instances. Project zonal metadata values
propagate to all VMs within the specified zone. Every VM has access to a
metadata server that you can use to query the configured project zonal
metadata values. To set metadata for individual instances, use gcloud
compute instances add-metadata. For information about metadata, see
https://cloud.google.com/compute/docs/metadata.

Only the metadata keys that you provide in the command get mutated. All
other existing metadata entries remain the same.

**Synopsis:**
```
gcloud compute project-zonal-metadata add
    --metadata=KEY=VALUE,[KEY=VALUE,...] --zone=ZONE [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--metadata` | KEY=VALUE,[KEY=VALUE,...] |  | The project zonal metadata key-value pairs that you want to add or update |
| `--zone` | ZONE |  | The zone in which you want to add or update project zonal metadata |


**Examples:**
```bash
To set the project zonal metadata with key=value in the zone us-central1-a
for the project my-gcp-project, run:

    $ gcloud compute project-zonal-metadata add --metadata=key=value \
        --zone=us-central1-a --project=my-gcp-project

For more information and examples for setting project zonal metadata, see
https://cloud.google.com/compute/docs/metadata/setting-custom-metadata#set-custom-project-zonal-metadata
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/project-zonal-metadata/add)

---
### `gcloud compute project-zonal-metadata describe`

Describe project zonal metadata

Describe project zonal metadata.

**Synopsis:**
```
gcloud compute project-zonal-metadata describe --zone=ZONE
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone for project zonal metadata |


**Examples:**
```bash
To describe the project zonal metadata in the zone us-central1-a for the
project my-gcp-project, run:

    $ gcloud compute project-zonal-metadata describe \
        --zone=us-central1-a --project=my-gcp-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/project-zonal-metadata/describe)

---
### `gcloud compute project-zonal-metadata remove`

Remove project zonal metadata

gcloud compute project-zonal-metadata remove is used to remove project
zonal metadata from all VMs within the specified zone. For information
about metadata, see https://cloud.google.com/compute/docs/metadata.

Only the metadata keys that you provide in the command get removed. All
other existing metadata entries remain the same.

After you remove a specific project zonal metadata entry, if that metadata
key has any project-wide value configured, then the VMs in the zone
automatically inherit that project-wide value.

**Synopsis:**
```
gcloud compute project-zonal-metadata remove --zone=ZONE
    [--all | --keys=KEY,[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | The zone in which you want to remove project zonal metadata |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[At most one of these can be specified:]_ If provided, all project zonal metadata entries are removed from VM instances in the zone. |
| `--keys` | KEY,[KEY,...] |  | _[At most one of these can be specified:]_ The keys for which you want to remove project zonal metadata |


**Examples:**
```bash
To remove the project zonal metadata with key=value in the zone
us-central1-a for the project my-gcp-project, run:

    $ gcloud compute project-zonal-metadata remove --keys=key \
        --zone=us-central1-a --project=my-gcp-project

For more information and examples about how to remove project zonal
metadata, see
https://cloud.google.com/compute/docs/metadata/setting-custom-metadata#remove-custom-project-zonal-metadata
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/project-zonal-metadata/remove)

---