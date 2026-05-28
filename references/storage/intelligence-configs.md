# gcloud storage intelligence-configs

manage Cloud Storage Intelligence Configurations

### `gcloud storage intelligence-configs describe`

Describes storage intelligence configuration

Describe storage intelligence config for the organization, sub-folder or
project.

**Synopsis:**
```
gcloud storage intelligence-configs describe
    (--organization=ORGANIZATION | --project=PROJECT
      | --sub-folder=SUB_FOLDER) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Specifies organization id for the storage intelligence config. |
| `--project` | PROJECT |  | _[Exactly one of these must be specified:]_ Specifies project for the storage intelligence config. |
| `--sub-folder` | SUB_FOLDER |  | _[Exactly one of these must be specified:]_ Specifies sub-folder id for the storage intelligence config. |


**Examples:**
```bash
The following command describes storage intelligence config for the
sub-folder with id 123456.

    $ gcloud storage intelligence-configs describe --sub-folder=123456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/intelligence-configs/describe)

---
### `gcloud storage intelligence-configs disable`

Disables storage intelligence

Disable storage intelligence for the organization, sub-folder or project.

**Synopsis:**
```
gcloud storage intelligence-configs disable
    (--organization=ORGANIZATION | --project=PROJECT
      | --sub-folder=SUB_FOLDER) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Specifies organization id for the storage intelligence config. |
| `--project` | PROJECT |  | _[Exactly one of these must be specified:]_ Specifies project for the storage intelligence config. |
| `--sub-folder` | SUB_FOLDER |  | _[Exactly one of these must be specified:]_ Specifies sub-folder id for the storage intelligence config. |


**Examples:**
```bash
The following command disables storage intelligence for the project.

    $ gcloud storage intelligence-configs disable --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/intelligence-configs/disable)

---
### `gcloud storage intelligence-configs enable`

Enables storage intelligence

Enable storage intelligence plan for the organization, sub-folder or
project along with filters. The command sets STANDARD edition by default if
no other edition flags like ``--trial-edition`` are specified.

**Synopsis:**
```
gcloud storage intelligence-configs enable
    (--organization=ORGANIZATION | --project=PROJECT
      | --sub-folder=SUB_FOLDER)
    [--trial-edition
      --exclude-bucket-id-regexes=[EXCLUDE_BUCKET_ID_REGEXES,...]
      | --include-bucket-id-regexes=[INCLUDE_BUCKET_ID_REGEXES,...]
      --exclude-locations=[EXCLUDE_LOCATIONS,...]
      | --include-locations=[INCLUDE_LOCATIONS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Specifies organization id for the storage intelligence config. |
| `--project` | PROJECT |  | _[Exactly one of these must be specified:]_ Specifies project for the storage intelligence config. |
| `--sub-folder` | SUB_FOLDER |  | _[Exactly one of these must be specified:]_ Specifies sub-folder id for the storage intelligence config. |


**Examples:**
```bash
To remove buckets from the storage intelligence plan, Use the following
command with --exclude-bucket-id-regexes flag. to specify list of bucket id
regexes.,

    $ gcloud storage intelligence-configs enable --organization=my-org \
        --exclude-bucket-id-regexes="my-bucket-.*"

To apply location based filters in the storage intelligence plan, Use
--include-locations or --exclude-locations flags to specify allowed list of
locations or excluded list of locations. The following command updates
storage intelligence plan of sub-folder 123456 with the specified list of
included locations.,

    $ gcloud storage intelligence-configs enable --sub-folder=123456 \
        --include-locations="us-east1","us-west1"

The following command enables storage intelligence with Trial edition for
the given project,

    $ gcloud storage intelligence-configs enable --project=my-project \
        --trial-edition
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/intelligence-configs/enable)

---
### `gcloud storage intelligence-configs update`

Updates storage intelligence configuration

Update storage intelligence configuration for the organization, sub-folder
or project. The command sets STANDARD edition by default if no other
edition flags like ``--trial-edition`` or ``--inherit-from-parent`` are
specified.

**Synopsis:**
```
gcloud storage intelligence-configs update
    (--organization=ORGANIZATION | --project=PROJECT
      | --sub-folder=SUB_FOLDER)
    (--inherit-from-parent | --trial-edition
      --exclude-bucket-id-regexes=[EXCLUDE_BUCKET_ID_REGEXES,...]
      | --include-bucket-id-regexes=[INCLUDE_BUCKET_ID_REGEXES,...]
      --exclude-locations=[EXCLUDE_LOCATIONS,...]
      | --include-locations=[INCLUDE_LOCATIONS,...]) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Specifies organization id for the storage intelligence config. |
| `--project` | PROJECT |  | _[Exactly one of these must be specified:]_ Specifies project for the storage intelligence config. |
| `--sub-folder` | SUB_FOLDER |  | _[Exactly one of these must be specified:]_ Specifies sub-folder id for the storage intelligence config. |
| `--inherit-from-parent` |  |  | _[Exactly one of these must be specified:]_ Specifies storage intelligence config to be inherited from parent. |
| `--trial-edition` |  |  | _[Exactly one of these must be specified:]_ Enables Storage Intelligence for TRIAL edition. |


**Examples:**
```bash
To limit buckets in the storage intelligence configuration, Use the
following command with --include-bucket-id-regexes flag. to specify list of
bucket ids and bucket id regexes.,

    $ gcloud storage intelligence-configs update --organization=my-org \
        --include-bucket-id-regexes=my-bucket-.*

To apply location based filters in the storage intelligence configuration,
Use --include-locations or --exclude-locations flags to specify allowed
list of locations or excluded list of locations. The following command
updates storage intelligence configuration of sub-folder 123456 with the
specified list of excluded locations.,

    $ gcloud storage intelligence-configs update --sub-folder=123456 \
        --exclude-locations=us-east1,us-west1

The following command updates storage intelligence for the given project by
inheriting existing storage intelligence configuration from the
hierarchical parent resource.,

    $ gcloud storage intelligence-configs update --project=my-project \
        --inherit-from-parent

To clear included locations from the project storage intelligence, Use the
following command.,

    $ gcloud storage intelligence-configs update --project=my-project \
        --include-locations=
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/intelligence-configs/update)

---