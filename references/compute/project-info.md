# gcloud compute project-info

read and manipulate project-level data like quotas and metadata

### `gcloud compute project-info add-metadata`

Add or update project-wide metadata

gcloud compute project-info add-metadata can be used to add or update
project-wide metadata. Every instance has access to a metadata server that
can be used to query metadata that has been set through this tool.
Project-wide metadata entries are visible to all instances. To set metadata
for individual instances, use gcloud compute instances add-metadata. For
information on metadata, see https://cloud.google.com/compute/docs/metadata

Only metadata keys that are provided are mutated. Existing metadata entries
will remain unaffected.

If you are using this command to manage SSH keys for your project, please
note the risks
(https://cloud.google.com/compute/docs/instances/adding-removing-ssh-keys#risks)
of manual SSH key management as well as the required format for SSH key
metadata, available at
https://cloud.google.com/compute/docs/instances/adding-removing-ssh-keys

**Synopsis:**
```
gcloud compute project-info add-metadata
    [--metadata=KEY=VALUE,[KEY=VALUE,...]]
    [--metadata-from-file=KEY=LOCAL_FILE_PATH,[...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--metadata` | KEY=VALUE,[KEY=VALUE,...] |  | Metadata to be made available to the guest operating system running on the instances. Each metadata entry is a key/value pair separated by an equals sign. Each metadata key must be unique and have a max of 128 bytes in length. Each value must have a max of 256 KB in length. Multiple arguments can be passed to this flag, e.g., --metadata key-1=value-1,key-2=value-2,key-3=value-3. The combined total size for all metadata entries is 512 KB. In images that have Compute Engine tools installed on them, such as the official images (https://cloud.google.com/compute/docs/images), the following metadata keys have special meanings: startup-script Specifies a script that will be executed by the instances once they start running. For convenience, --metadata-from-file can be used to pull the value from a file. startup-script-url Same as startup-script except that the script contents are pulled from a publicly-accessible location on the web. For startup scripts on Windows instances, the following metadata keys have special meanings: windows-startup-script-url, windows-startup-script-cmd, windows-startup-script-bat, windows-startup-script-ps1, sysprep-specialize-script-url, sysprep-specialize-script-cmd, sysprep-specialize-script-bat, and sysprep-specialize-script-ps1. For more information, see Running startup scripts (https://cloud.google.com/compute/docs/startupscript). At least one of [--metadata] or [--metadata-from-file] is required. |
| `--metadata-from-file` | KEY=LOCAL_FILE_PATH,[...] |  | Same as --metadata except that the value for the entry will be read from a local file. This is useful for values that are too large such as startup-script contents. At least one of [--metadata] or [--metadata-from-file] is required. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/project-info/add-metadata)

---
### `gcloud compute project-info describe`

Describe the Compute Engine project resource

gcloud compute project-info describe displays all data associated with the
Compute Engine project resource. The project resource contains data such as
global quotas, common instance metadata, and the project's creation time.

**Synopsis:**
```
gcloud compute project-info describe [GCLOUD_WIDE_FLAG ...]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/project-info/describe)

---
### `gcloud compute project-info remove-metadata`

Remove project-wide metadata entries

gcloud compute project-info remove-metadata can be used to remove
project-wide metadata entries.

**Synopsis:**
```
gcloud compute project-info remove-metadata [--all | --keys=KEY,[KEY,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[At most one of these can be specified:]_ If provided, all metadata entries are removed. |
| `--keys` | KEY,[KEY,...] |  | _[At most one of these can be specified:]_ The keys of the entries to remove. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/project-info/remove-metadata)

---
### `gcloud compute project-info set-usage-bucket`

Set usage reporting bucket for a project

(DEPRECATED) Set usage reporting bucket for a project.

This command is deprecated. Please onboard with BigQuery Export instead.
https://docs.cloud.google.com/billing/docs/how-to/export-data-bigquery

gcloud compute project-info set-usage-bucket configures usage reporting for
projects.

Setting usage reporting will cause a log of usage per resource to be
written to a specified Google Cloud Storage bucket daily.

For example, to write daily logs of the form usage_gce_YYYYMMDD.csv to the
bucket my-bucket, run:

    $ gcloud compute project-info set-usage-bucket \
        --bucket=gs://my-bucket

To disable this feature, issue the command:

    $ gcloud compute project-info set-usage-bucket --no-bucket

**Synopsis:**
```
gcloud compute project-info set-usage-bucket
    (--bucket=BUCKET | --no-bucket) [--prefix=PREFIX]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | _[Exactly one of these must be specified:]_ Name of an existing Google Cloud Storage bucket where the usage report object should be stored. This can either be the bucket name by itself, such as my-bucket, or the bucket name with gs:// or https://storage.googleapis.com/ in front of it, such as gs://my-bucket. The Google Service Account for performing usage reporting is granted write access to this bucket. The user running this command must be an owner of the bucket. To clear the usage bucket, use --no-bucket. |
| `--no-bucket` |  |  | _[Exactly one of these must be specified:]_ Unsets the bucket. This disables usage report storage. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--prefix` | PREFIX |  | Optional prefix for the name of the usage report object stored in the bucket. If not supplied, then this defaults to usage. The report is stored as a CSV file named PREFIX_gce_YYYYMMDD.csv where YYYYMMDD is the day of the usage according to Pacific Time. The prefix should conform to Google Cloud Storage object naming conventions. This flag must not be provided when clearing the usage bucket. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/project-info/set-usage-bucket)

---
### `gcloud compute project-info update`

Update a Compute Engine project resource

gcloud compute project-info update is used to update a Compute Engine
project resource.

**Synopsis:**
```
gcloud compute project-info update [--cloud-armor-tier=CLOUD_ARMOR_TIER]
    [--default-network-tier=DEFAULT_NETWORK_TIER] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cloud-armor-tier` | one of: CA_STANDARD, CA_ENTERPRISE_PAYGO, CA_ENTERPRISE_ANNUAL |  | Cloud armor tier to assign to the project. CLOUD_ARMOR_TIER must be one of: CA_STANDARD, CA_ENTERPRISE_PAYGO, CA_ENTERPRISE_ANNUAL. |
| `--default-network-tier` | one of: PREMIUM, STANDARD |  | The default network tier to assign to the project. DEFAULT_NETWORK_TIER must be one of: PREMIUM, STANDARD. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/project-info/update)

---