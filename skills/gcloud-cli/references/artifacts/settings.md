# gcloud artifacts settings

manage Artifact Registry project settings

### `gcloud artifacts settings describe`

List all Artifact Registry project settings

List all Artifact Registry project settings.

**Synopsis:**
```
gcloud artifacts settings describe [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list project settings for project my-project:

    $ gcloud artifacts settings describe --project=my-package
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/settings/describe)

---
### `gcloud artifacts settings disable-upgrade-redirection`

Disables redirection from Container Registry to Artifact Registry

Disables redirection from Container Registry to Artifact Registry.

**Synopsis:**
```
gcloud artifacts settings disable-upgrade-redirection
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To disable redirection for project my-project:

    $ gcloud artifacts settings disable-upgrade-redirection \
       --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/settings/disable-upgrade-redirection)

---
### `gcloud artifacts settings enable-upgrade-redirection`

Enables redirection from Container Registry to Artifact Registry

Enables redirection from Container Registry to Artifact Registry.

**Synopsis:**
```
gcloud artifacts settings enable-upgrade-redirection [--dry-run]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dry-run` |  |  | Validate the project setup, but do not enable redirection |


**Examples:**
```bash
To enable redirection for project my-project:

    $ gcloud artifacts settings enable-upgrade-redirection \
       --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/settings/enable-upgrade-redirection)

---