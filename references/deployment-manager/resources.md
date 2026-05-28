# gcloud deployment-manager resources

commands for Deployment Manager resources

### `gcloud deployment-manager resources describe`

Provide information about a resource

This command prints out all available details about a resource.

**Synopsis:**
```
gcloud deployment-manager resources describe RESOURCE
    [--deployment=DEPLOYMENT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE
   Resource name.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deployment` | DEPLOYMENT |  | Deployment name |


**Examples:**
```bash
To display information about a resource, run:

    $ gcloud deployment-manager resources describe \
        --deployment=my-deployment my-resource-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/resources/describe)

---
### `gcloud deployment-manager resources list`

List resources in a deployment

Prints a table with summary information on all resources in the deployment.

**Synopsis:**
```
gcloud deployment-manager resources list [--deployment=DEPLOYMENT]
    [--simple-list] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deployment` | DEPLOYMENT |  | Deployment name |
| `--simple-list` |  |  | Changes the --format flag to print the resource IDs. Otherwise either the --format value or the default format is used. |


**Examples:**
```bash
To print out a list of resources in the deployment with some summary
information about each, run:

    $ gcloud deployment-manager resources list --deployment=my-deployment

To print only the name of each resource, run:

    $ gcloud deployment-manager resources list \
        --deployment=my-deployment --simple-list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/resources/list)

---