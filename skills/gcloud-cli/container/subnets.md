# gcloud container subnets

manage subnets to be used by Google Kubernetes Engine clusters

### `gcloud container subnets list-usable`

List subnets usable for cluster creation in a specific project

Usability of subnetworks for cluster creation is dependent on the IAM
policy of the project's Google Kubernetes Engine Service Account. Use the
--project flag to evaluate subnet usability in different projects. This
list may differ from the list returned by Google Compute Engine's
list-usable command, which returns subnets only usable by the caller.

To show subnetworks shared from a Shared-VPC host project, use
--network-project to specify the project that owns the subnetworks.

**Synopsis:**
```
gcloud container subnets list-usable [--network-project=NETWORK_PROJECT]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network-project` | NETWORK_PROJECT |  | The project owning the subnetworks returned. This field is translated into the expression networkProjectId=[PROJECT_ID] and ANDed to the --filter flag value. Defaults to the --project value. |


**Examples:**
```bash
List all subnetworks usable for cluster creation in project my-project.

    $ gcloud container subnets list-usable --project=my-project

List all subnetworks existing in project my-shared-host-project usable for
cluster creation in project my-service-project.

    $ gcloud container subnets list-usable \
      --project=my-service-project \
      --network-project=my-shared-host-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/subnets/list-usable)

---