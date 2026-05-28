# gcloud logging settings

manages the org settings for the Cloud Logging Logs Router

### `gcloud logging settings describe`

Display the settings for the Cloud Logging Logs Router

If kmsKeyName is present in the output, then CMEK is enabled for your
project, folder, organization or billing-account. You can also find the
Logs Router service account using this command.

**Synopsis:**
```
gcloud logging settings describe
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the settings to describe. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the settings to describe. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the settings to describe. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the settings to describe. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To describe the Logs Router settings for a project, run:

    $ gcloud logging settings describe --project=[PROJECT_ID]

To describe the Logs Router settings for an organization, run:

    $ gcloud logging settings describe --organization=[ORGANIZATION_ID]

    kmsKeyName:
    'projects/my-project/locations/my-location/keyRings/my-keyring/cryptoKeys/key'
    name: 'organizations/[ORGANIZATION_ID]/settings'
    serviceAccountId:
    '[SERVICE_ACCOUNT_ID]@gcp-sa-logging.iam.gserviceaccount.com'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/settings/describe)

---
### `gcloud logging settings update`

Update the settings for the Cloud Logging Logs Router

Use this command to update the --kms-key-name, --storage-location,
--disable-default-sink and --analytics-mode associated with the Cloud
Logging Logs Router.

The Cloud KMS key must already exist and Cloud Logging must have permission
to access it.

The storage location must be allowed by Org Policy.

Customer-managed encryption keys (CMEK) for the Logs Router can currently
only be configured at the organization-level and will apply to all projects
in the organization.

**Synopsis:**
```
gcloud logging settings update
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID)
    [--disable-default-sink] [--storage-location=STORAGE_LOCATION]
    [--clear-kms-key | [--kms-key-name=KMS_KEY_NAME
      : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder to update Logs Router settings for. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization to update Logs Router settings for. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--disable-default-sink` |  |  | Enable or disable _Default sink for the _Default bucket. Specify --no-disable-default-sink to enable a disabled _Default sink. Note: It only applies to the newly created projects and will not affect the projects created before. |
| `--storage-location` | STORAGE_LOCATION |  | Update the storage location for _Default bucket and _Required bucket. Note: It only applies to the newly created projects and will not affect the projects created before. |


**Examples:**
```bash
To enable CMEK for the Logs Router for an organization, run:

    $ gcloud logging settings update --organization=[ORGANIZATION_ID] \
        --kms-key-name='projects/my-project/locations/my-location/keyRin\
    gs/my-keyring/cryptoKeys/key'

To disable CMEK for the Logs Router for an organization, run:

    $ gcloud logging settings update --organization=[ORGANIZATION_ID] \
        --clear-kms-key

To update storage location for the Logs Router for an organization, run:

    $ gcloud logging settings update --organization=[ORGANIZATION_ID] \
        --storage-location=[LOCATION_ID]

To update storage location for the Logs Router for a folder, run:

    $ gcloud logging settings update --folder=[FOLDER_ID] \
        --storage-location=[LOCATION_ID]

To disable default sink for the Logs Router for an organization, run:

    $ gcloud logging settings update --organization=[ORGANIZATION_ID] \
        --disable-default-sink=true

To enable default sink for the Logs Router for an organization, run:

    $ gcloud logging settings update --organization=[ORGANIZATION_ID] \
        --disable-default-sink=false

To enable analytics for the log buckets under an organization, run:

    $ gcloud logging settings update --organization=[ORGANIZATION_ID] \
        --disable-default-sink=false --analytics-mode=required
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/settings/update)

---