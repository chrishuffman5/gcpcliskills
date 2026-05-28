# gcloud resource-manager capabilities

manage Cloud Folder Capabilities

### `gcloud resource-manager capabilities describe`

Show whether a Capability is enabled

Command to show whether a Capability is enabled.

This command can fail for the following reasons:
  o The capability specified does not exist.
  o The active account does not have permission to access the given
    folder/capability.

**Synopsis:**
```
gcloud resource-manager capabilities describe CAPABILITY_ID
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CAPABILITY_ID
   ID for the capability you want to describe.
```

**Examples:**
```bash
The following command prints metadata for a capability with the ID
folders/123/capabilities/app-management:

    $ gcloud resource-manager capabilities describe \
        "folders/123/capabilities/app-management"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/capabilities/describe)

---
### `gcloud resource-manager capabilities update`

Update a folder capability

Command to Update/Set the value field of the Folder capability. This can be
done by using the --enable flag to set the value to True, and the
--no-enable flag to set the value to False.

This command can fail for the following reasons:
  o There is no folder parenting the given capability name.
  o The active account does not have permission to update the given
    folder/capability.

**Synopsis:**
```
gcloud resource-manager capabilities update CAPABILITY_ID --[no-]enable
    [--update-mask=UPDATE_MASK] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CAPABILITY_ID
   ID for the capability you want to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]enable` |  |  | Enable the Capability. Use --enable to enable and --no-enable to disable. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-mask` | UPDATE_MASK |  | Update Mask. This is an optional field, and the only valid value this can be set to currently is "value". |


**Examples:**
```bash
The following command updates a capability with the ID
folders/123/capabilities/app-management to have the value True:

    $ gcloud resource-manager capabilities update \
        "folders/123/capabilities/app-management" --enable

In order to set the value to False, the following command can be used:

    $ gcloud resource-manager capabilities update \
        "folders/123/capabilities/app-management" --no-enable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/capabilities/update)

---