# gcloud kms autokey-config

update and retrieve the AutokeyConfig

### `gcloud kms autokey-config describe`

Describe the AutokeyConfig of a folder

gcloud kms autokey-config describe can be used to retrieve the
AutokeyConfig of a folder.

**Synopsis:**
```
gcloud kms autokey-config describe --folder=FOLDER [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | The folder id in which the AutokeyConfig resource exists. |


**Examples:**
```bash
The following command retrieves the AutokeyConfig of a folder having
folder-id 123:

    $ gcloud kms autokey-config describe --folder=123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/autokey-config/describe)

---
### `gcloud kms autokey-config show-effective-config`

Gets the effective Cloud KMS AutokeyConfig for a given project

gcloud kms autokey-config show-effective-config can be used to get the
effective Cloud KMS AutokeyConfig for a given project.

**Synopsis:**
```
gcloud kms autokey-config show-effective-config [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command retrieves the effective Cloud KMS AutokeyConfig for a
given project my-project:

    $ gcloud kms autokey-config show-effective-config \
        --project=my-project

If --project flag is not provided, then the current project will be used.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/autokey-config/show-effective-config)

---
### `gcloud kms autokey-config update`

Updates the AutokeyConfig for a folder

gcloud kms autokey-config update can be used to update the AutokeyConfig of
a folder.

**Synopsis:**
```
gcloud kms autokey-config update CONFIG_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CONFIG_FILE
   The file containing the AutokeyConfig resource.
```

**Examples:**
```bash
The following command updates the AutokeyConfig for the folder mentioned in
the config.yaml file:

    $ gcloud kms autokey-config update config.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/autokey-config/update)

---