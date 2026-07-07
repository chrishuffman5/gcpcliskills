# gcloud apigee environments

manage Apigee environments

### `gcloud apigee environments list`

List Apigee deployment environments

List Apigee deployment environments.

**Synopsis:**
```
gcloud apigee environments list [--organization=ORGANIZATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[organization will be used. This represents a Cloud resource.]_ ID of the organization or fully qualified identifier for the organization. To set the organization attribute: + provide the argument --organization on the command line; + set the property [project] or provide the argument [--project] on the command line, using a Cloud Platform project with an associated Apigee organization. |


**Examples:**
```bash
To list all environments for the active Cloud Platform project, run:

    $ gcloud apigee environments list

To get a JSON array of all environments in an organization called my-org,
run:

    $ gcloud apigee environments list --organization=my-org --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/environments/list)

---