# gcloud asset operations

manage Cloud Asset Inventory operations

### `gcloud asset operations describe`

Describe a Cloud Asset Inventory operation

Describe a Cloud Asset Inventory operation.

**Synopsis:**
```
gcloud asset operations describe OPERATION_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION_NAME
   Name of the operation to describe.
```

**Examples:**
```bash
To describe the operation
'projects/19306908007/operations/ExportAssets/RESOURCE/78689643348272423423',
run:

    $ gcloud asset operations describe \
        projects/19306908007/operations/ExportAssets/RESOURCE/\
    78689643348272423423
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/operations/describe)

---