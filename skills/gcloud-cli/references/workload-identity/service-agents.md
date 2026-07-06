# gcloud workload-identity service-agents

manage Service Agents for Workload Identity

### `gcloud workload-identity service-agents generate`

Generate service agents for a service producer

Generates service agents for a specified service producer within a project, folder, or organization at a given location. The response includes the service agent details (email addresses) and the associated roles that you must then grant manually.

**Synopsis:**
```
gcloud workload-identity service-agents generate --service=SERVICE
    (--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT)
    [--location=LOCATION; default="global"] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE |  | _[This must be specified.]_ The service producer to generate service agents for, given as the API endpoint (e.g. `bigquery.googleapis.com`). |
| `--folder` | FOLDER |  | _[Exactly one of --folder / --organization / --project must be specified.]_ The folder number to generate service agents for. |
| `--organization` | ORGANIZATION |  | _[Exactly one of --folder / --organization / --project must be specified.]_ The organization number to generate service agents for. |
| `--project` | PROJECT |  | _[Exactly one of --folder / --organization / --project must be specified.]_ The project number to generate service agents for. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | `global` | The location to generate service agents in. |

**Examples:**
```bash
To generate agents for BigQuery in the global location for project 123456, run:

    $ gcloud workload-identity service-agents generate \
        --service="bigquery.googleapis.com" \
        --location="global" \
        --project="123456"

To generate agents for BigQuery in the global location for folder 123456, run:

    $ gcloud workload-identity service-agents generate \
        --service="bigquery.googleapis.com" \
        --location="global" \
        --folder="123456"

To generate agents for BigQuery in the global location for organization 123456, run:

    $ gcloud workload-identity service-agents generate \
        --service="bigquery.googleapis.com" \
        --location="global" \
        --organization="123456"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workload-identity/service-agents/generate)

---
