# gcloud access-approval service-account

manage Access Approval service account

### `gcloud access-approval service-account get`

Get Access Approval service account

Retrieves the service account that is used by Access Approval to access KMS
keys for signing approved approval requests.

**Synopsis:**
```
gcloud access-approval service-account get
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[At most one of these can be specified:]_ Folder number. Only one of --project, --folder, or --organization can be provided. If none are provided then it uses config property [core/project]. |
| `--organization` | ORGANIZATION |  | _[At most one of these can be specified:]_ Organization number. Either --project, --folder, or --organization must be provided. If none are provided then it uses config property [core/project]. |
| `--project` | PROJECT |  | _[At most one of these can be specified:]_ Project number or id. Only one of --project, --folder, or --organization can be provided. If none are provided then it uses config property [core/project]. |


**Examples:**
```bash
To get the service account for the current project use

    $ gcloud access-approval service-account get

To get the service account for folder f1 use

    $ gcloud access-approval service-account get --folder=f1

To get the service account for organization org1 use

    $ gcloud access-approval service-account get --organization=org1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-approval/service-account/get)

---