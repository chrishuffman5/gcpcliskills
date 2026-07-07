# gcloud deployment-manager manifests

commands for Deployment Manager manifests

### `gcloud deployment-manager manifests describe`

Provide information about a manifest

This command prints out all available details about a manifest.

**Synopsis:**
```
gcloud deployment-manager manifests describe [MANIFEST]
    --deployment=DEPLOYMENT [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[MANIFEST]
   Manifest name.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deployment` | DEPLOYMENT |  | Deployment name. |


**Examples:**
```bash
To display information about a manifest, run:

    $ gcloud deployment-manager manifests describe \
        --deployment=my-deployment manifest-name

To display information about the latest manifest, run:

    $ gcloud deployment-manager manifests describe \
        --deployment=my-deployment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/manifests/describe)

---
### `gcloud deployment-manager manifests list`

List manifests in a deployment

Prints a table with summary information on all manifests in the deployment.

**Synopsis:**
```
gcloud deployment-manager manifests list --deployment=DEPLOYMENT
    [--simple-list] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deployment` | DEPLOYMENT |  | Deployment name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--simple-list` |  |  | Changes the --format flag to print the resource IDs. Otherwise either the --format value or the default format is used. |


**Examples:**
```bash
To print out a list of manifests in a deployment, run:

    $ gcloud deployment-manager manifests list --deployment=my-deployment

To print only the name of each manifest, run:

    $ gcloud deployment-manager manifests list \
        --deployment=my-deployment --simple-list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/manifests/list)

---