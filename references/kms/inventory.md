# gcloud kms inventory

manages the KMS Inventory and Key Tracking commands

### `gcloud kms inventory get-protected-resources-summary`

Gets the protected resources summary

gcloud kms inventory get-protected-resources-summary returns a summary of
the resources a key is protecting.

The summary includes how many projects contain protected resources, how
many protected resources there are, what are the types of protected
resources, and the count for each type of protected resource.

**Synopsis:**
```
gcloud kms inventory get-protected-resources-summary
    (--keyname=KEYNAME : --keyring=KEYRING --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--keyname` | KEYNAME |  | _[This must be specified.]_ ID of the key or fully qualified identifier for the key. To set the key attribute: + provide the argument --keyname on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--keyring` | KEYRING |  | _[This must be specified.]_ The KMS keyring of the key. To set the keyring attribute: + provide the argument --keyname on the command line with a fully specified name; + provide the argument --keyring on the command line. |
| `--location` | LOCATION |  | _[This must be specified.]_ The Google Cloud location for the key. To set the location attribute: + provide the argument --keyname on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To view the summary of protected resources for the key puppy, run:

    $ gcloud kms inventory get-protected-resources-summary \
        --keyname=puppy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/inventory/get-protected-resources-summary)

---
### `gcloud kms inventory list-keys`

Lists the keys in a project

gcloud kms inventory list-keys lists the keys in the specified project.

**Synopsis:**
```
gcloud kms inventory list-keys [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To view the keys in the default project, run:

    $ gcloud kms inventory list-keys

To view the keys in project jellyfish, run:

    $ gcloud kms inventory list-keys --project=jellyfish
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/inventory/list-keys)

---
### `gcloud kms inventory search-protected-resources`

Searches the resources protected by a key

gcloud kms inventory search-protected-resources returns a list of the
resources a key is protecting within the specified organization.

**Synopsis:**
```
gcloud kms inventory search-protected-resources --scope=ORGANIZATION_ID
    (--keyname=KEYNAME : --keyring=KEYRING --location=LOCATION)
    [--resource-types=[RESOURCE_TYPES,...]] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--scope` | ORGANIZATION_ID |  | Organization ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resource-types` | [RESOURCE_TYPES,...] |  | A list of resource types that this request searches for. If empty, it will search all the trackable resource types (https://cloud.google.com/kms/docs/view-key-usage#tracked-resource-types). Regular expressions are also supported. For example: * compute.googleapis.com.* snapshots resources whose type starts with compute.googleapis.com. * .*Image snapshots resources whose type ends with Image. * .*Image.* snapshots resources whose type contains Image. See RE2 (https://github.com/google/re2/wiki/Syntax) for all supported regular expression syntax. If the regular expression does not match any supported resource type, an INVALID_ARGUMENT error will be returned. |


**Examples:**
```bash
To view the protected resources for the key puppy and organization number
1234 run:

    $ gcloud kms inventory search-protected-resources --keyname=puppy \
        --scope=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/inventory/search-protected-resources)

---