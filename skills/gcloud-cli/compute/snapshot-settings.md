# gcloud compute snapshot-settings

describe and update Compute Engine snapshot settings

### `gcloud compute snapshot-settings describe`

Describe snapshot settings

Describe the snapshot settings of a project.

**Synopsis:**
```
gcloud compute snapshot-settings describe [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To display the snapshot settings of a project called my-project, run:

    $ gcloud compute snapshot-settings describe --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/snapshot-settings/describe)

---
### `gcloud compute snapshot-settings update`

Update snapshot settings

Update the snapshot settings of a project.

**Synopsis:**
```
gcloud compute snapshot-settings update [--async]
    [--storage-location-names=[STORAGE_LOCATION_NAMES,...]]
    [--storage-location-policy=STORAGE_LOCATION_POLICY]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--storage-location-names` | [STORAGE_LOCATION_NAMES,...] |  | The custom storage location that you specify for the project's snapshots. You can specify only a single location. Use this flag only when you use the specific-locations value for the --storage-location-policy flag. For more information, refer to the snapshot settings documentation at https://cloud.google.com/compute/docs/disks/snapshot-settings. |
| `--storage-location-policy` | one of: local-region, nearest-multi-region, specific-locations |  | The storage location policy. For more information, refer to the snapshot settings documentation at https://cloud.google.com/compute/docs/disks/snapshot-settings. STORAGE_LOCATION_POLICY must be one of: local-region, nearest-multi-region, specific-locations. |


**Examples:**
```bash
To update the snapshot settings and set the storage location policy to the
nearest multi-region as the source disk, run:

    $ gcloud compute snapshot-settings update \
    --storage-location-policy=nearest-multi-region

To update the snapshot settings and set the storage location policy to the
same region as the source disk, run:

    $ gcloud compute snapshot-settings update \
    --storage-location-policy=local-region

To update the snapshot settings and set the storage location policy to
store snapshots in a specific location like us-west1, run:

    $ gcloud compute snapshot-settings update \
    --storage-location-policy=specific-locations \
    --storage-location-names=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/snapshot-settings/update)

---