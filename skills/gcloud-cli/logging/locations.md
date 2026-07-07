# gcloud logging locations

query Cloud Logging locations

### `gcloud logging locations describe`

Display information about a location

Displays information about a location.

**Synopsis:**
```
gcloud logging locations describe LOCATION_ID
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LOCATION_ID
   Id of the location to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the location to describe. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the location to describe. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the location to describe. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the location to describe. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To describe a location in a project, run:

    $ gcloud logging locations describe my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/locations/describe)

---
### `gcloud logging locations list`

List the availables location

Lists the available locations for Cloud Logging.

**Synopsis:**
```
gcloud logging locations list
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the locations to list. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the locations to list. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the locations to list. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the locations to list. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To list the available locations, run:

    $ gcloud logging locations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/locations/list)

---