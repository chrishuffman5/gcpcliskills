# gcloud looker instances

manage Looker instances

### `gcloud looker instances create`

Create a Looker instance

Create a new Looker instance.

This command can fail for the following reasons:
  o An instance with the same name already exists.
  o The active account does not have permission to create instances.
  o --async flag is not passed

**Synopsis:**
```
gcloud looker instances create (INSTANCE : --region=REGION)
    --edition=EDITION --oauth-client-id=OAUTH_CLIENT_ID
    --oauth-client-secret=OAUTH_CLIENT_SECRET [--async]
    [--class-type=CLASS_TYPE] [--fips-enabled] [--kms-key=KMS_KEY]
    [--no-public-ip-enabled]
    [--consumer-network=CONSUMER_NETWORK --private-ip-enabled
      : --reserved-range=RESERVED_RANGE]
    [--deny-maintenance-period-end-date=DENY_MAINTENANCE_PERIOD_END_DATE
      --deny-maintenance-period-start-date=DENY_MAINTENANCE_PERIOD_START_DATE --deny-maintenance-period-time=DENY_MAINTENANCE_PERIOD_TIME]
    [--maintenance-window-day=MAINTENANCE_WINDOW_DAY
      --maintenance-window-time=MAINTENANCE_WINDOW_TIME]
    [--psc-enabled : --psc-allowed-vpcs=[PSC_ALLOWED_VPCS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Looker instance
you want to create. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Looker region of the instance. Overrides the default
     looker/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property looker/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--edition` | one of: core-embed-annual A Looker (Google Cloud core) product for deploying and maintaining external analytics and custom applications at scale |  | The edition of the Looker instance. EDITION must be one of: core-embed-annual A Looker (Google Cloud core) product for deploying and maintaining external analytics and custom applications at scale. This can be purchased via an annual contract. core-enterprise-annual A Looker (Google Cloud core) product with enhanced security features for a wide variety of internal BI and analytics use cases. This can be purchased via an annual contract. core-standard A Looker (Google Cloud core) product for small organizations or teams with fewer than 50 users. This will be billed monthly while the instance is active. core-standard-annual A Looker (Google Cloud core) product for small organizations or teams with fewer than 50 users. This can be purchased via an annual contract. core-trial Trial edition of Looker. core-trial-embed An embed trial edition of Looker (Google Cloud core) product. core-trial-enterprise An enterprise trial edition of Looker (Google Cloud core) product. core-trial-standard A standard trial edition of Looker (Google Cloud core) product. nonprod-core-embed-annual A non-production edition of Looker (Google Cloud core) product for deploying and maintaining external analytics and custom applications at scale. This can be purchased via an annual contract. nonprod-core-enterprise-annual A non-production edition of Looker (Google Cloud core) product with enhanced security features for a wide variety of internal BI and analytics use cases. This can be purchased via an annual contract. nonprod-core-standard-annual A non-production edition of Looker (Google Cloud core) product for small organizations or teams with fewer than 50 users. This can be purchased via an annual contract. |
| `--oauth-client-id` | OAUTH_CLIENT_ID |  | The client ID from an external OAuth application. OAuth Application Credentials - Looker Instance OAuth login settings. Setup an OAuth app that will allow users to authenticate and access the instance. For more information see: https://developers.google.com/identity/protocols/oauth2/web-server#creatingcred |
| `--oauth-client-secret` | OAUTH_CLIENT_SECRET |  | The client secret from an external OAuth application. OAuth Application Credentials - Looker Instance OAuth login settings. Setup an OAuth app that will allow users to authenticate and access the instance. For more information see: https://developers.google.com/identity/protocols/oauth2/web-server#creatingcred |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--class-type` | one of: p1, r1 |  | The class type of the Looker instance. CLASS_TYPE must be one of: p1, r1. |
| `--fips-enabled` |  |  | This specifies whether FIPS is enabled on the Looker instance. |
| `--public-ip-enabled` |  |  | _[+ provide the argument --kms-key on the command line.]_ This specifies whether public IP is enabled on the Looker instance. Enabled by default, use --no-public-ip-enabled to disable. |


**Examples:**
```bash
To create a basic tier instance with the name my-looker-instance in region
us-central-1 with an edition of LOOKER_CORE_STANDARD, run:

    $ gcloud looker instances create my-looker-instance \
        --region=us-central1 --edition="core-standard" \
        --oauth-client-id='looker' --oauth-client-secret='looker' \
        --async

Note: It is recommended that the --async argument is provided when creating
a Looker instance.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/instances/create)

---
### `gcloud looker instances delete`

Delete a Looker instance

Delete a Looker instance.

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The active account does not have permission to access the given
    instance.

**Synopsis:**
```
gcloud looker instances delete (INSTANCE : --region=REGION) [--async]
    [--force] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Looker instance
you want to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Looker region of the instance. Overrides the default
     looker/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property looker/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | Force delete an instance. |


**Examples:**
```bash
To delete an instance with the name my-looker-instance in your default
region, run:

    $ gcloud looker instances delete my-looker-instance --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/instances/delete)

---
### `gcloud looker instances describe`

Show metadata for a Looker instance

Show metadata for a Looker instance.

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The active account does not have permission to access the given
    instance.

**Synopsis:**
```
gcloud looker instances describe (INSTANCE : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Looker instance
you want to describe. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Looker region of the instance. Overrides the default
     looker/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property looker/region.
```

**Examples:**
```bash
To display the metadata for an instance with the name my-looker-instance in
the default region, run:

    $ gcloud looker instances describe my-looker-instance

To display all fields of the instance metadata, add the --format=json flag:

    $ gcloud looker instances describe my-looker-instance --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/instances/describe)

---
### `gcloud looker instances export`

Export a Looker instance

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The active account does not have permission to access the given
    instance.
  o The Google Cloud Storage bucket does not exist.

**Synopsis:**
```
gcloud looker instances export (INSTANCE : --region=REGION)
    --kms-key=KMS_KEY --target-gcs-uri=TARGET_GCS_URI
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Looker instance
you want to export. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The region of the instance.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--kms-key` | KMS_KEY |  | _[This must be specified.]_ Fully qualified identifier (name) for the key. |
| `--target-gcs-uri` | TARGET_GCS_URI |  | _[This must be specified.]_ The path to the folder in Google Cloud Storage where the export will be stored. The URI is in the form gs://bucketName/folderName. The Looker Service Agent should have the role Storage Object Creator. |


**Examples:**
```bash
To export an instance with the name my-looker-instance in the default
region, run:

    $ gcloud looker instances export my-looker-instance \
        --target-gcs-uri='gs://bucketName/folderName' \
        --kms-key='projects/my-project/locations/us-central1/keyRings/my\
    -key-ring/cryptoKeys/my-key'

Note that the kms-key flag should be the full name of the kms key.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/instances/export)

---
### `gcloud looker instances import`

Import a Looker instance

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The active account does not have permission to access the given
    instance.
  o The Google Cloud Storage bucket does not exist.

**Synopsis:**
```
gcloud looker instances import (INSTANCE : --region=REGION)
    --source-gcs-uri=SOURCE_GCS_URI [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Looker instance
you want to import. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The region of the instance.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-gcs-uri` | SOURCE_GCS_URI |  | _[This must be specified.]_ The path to the folder in Google Cloud Storage where the import will be retrieved from. The URI is in the form gs://bucketName/folderName. |


**Examples:**
```bash
To import an instance with the name my-looker-instance in the default
region, run:

    $ gcloud looker instances import my-looker-instance \
        --source-gcs-uri='gs://bucketName/folderName'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/instances/import)

---
### `gcloud looker instances list`

List Looker instances

List all Looker instances under the specified project and region.

To specify the maximum number of instances to list, use the --limit flag.

**Synopsis:**
```
gcloud looker instances list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property looker/region. |


**Examples:**
```bash
To list up to five instances, run:

    $ gcloud looker instances list --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/instances/list)

---
### `gcloud looker instances restart`

Restart a Looker instance

Restart for a Looker instance.

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The active account does not have permission to access the given
    instance.

**Synopsis:**
```
gcloud looker instances restart (INSTANCE : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Looker instance
you want to describe. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Looker region of the instance. Overrides the default
     looker/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property looker/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To restart an instance with the name my-looker-instance in the default
region, run:

    $ gcloud looker instances restart my-looker-instance --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/instances/restart)

---
### `gcloud looker instances restore`

Restore a Looker instance from a backup

Restore a Looker instance from a backup.

The Looker instance in which the backup is derived from will be restored to
that specific backup.

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The backup specified does not exist.
  o The active account does not have permission to access the given
    instance and backups.

**Synopsis:**
```
gcloud looker instances restore (INSTANCE : --region=REGION)
    --backup=BACKUP [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Looker instance
you want to describe. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Looker region of the instance. Overrides the default
     looker/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property looker/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup` | BACKUP |  | The ID of the backup instance in the format projects/{project}/locations/{location}/instances/{instance}/backups/{backup} |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To restore a backup with id of 7e504e66-c389-4d8d-bca7-f710c6d96567 that
belongs to an instance named my-looker-instance, in the region us-central1,
run:

    $ gcloud looker instances restore my-looker-instance \
        --backup="7e504e66-c389-4d8d-bca7-f710c6d96567" \
        --region="us-central1" --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/instances/restore)

---
### `gcloud looker instances update`

Update a Looker instance

Update the metadata and/or configuration parameters of a Looker instance.

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The active account does not have permission to update the given
    instance.

**Synopsis:**
```
gcloud looker instances update (INSTANCE : --region=REGION)
    [--allowed-email-domains=[ALLOWED_EMAIL_DOMAINS,...]] [--async]
    [--class-type=CLASS_TYPE] [--custom-domain=CUSTOM_DOMAIN]
    [--linked-lsp-project-number=LINKED_LSP_PROJECT_NUMBER]
    [--public-ip-enabled]
    [--add-developer-users=ADD_DEVELOPER_USERS
      --add-standard-users=ADD_STANDARD_USERS
      --add-viewer-users=ADD_VIEWER_USERS]
    [--clear-periodic-export-config
      | --periodic-export-gcs-uri=PERIODIC_EXPORT_GCS_URI
      --periodic-export-kms-key=PERIODIC_EXPORT_KMS_KEY
      --periodic-export-start-time=PERIODIC_EXPORT_START_TIME]
    [--clear-psc-allowed-vpcs | --psc-allowed-vpcs=[PSC_ALLOWED_VPCS,...]
      --clear-psc-service-attachments
      | --psc-service-attachment=[attachment=ATTACHMENT],
      [domain=DOMAIN],[multiple-domains=MULTIPLE-DOMAINS]]
    [--deny-maintenance-period-end-date=DENY_MAINTENANCE_PERIOD_END_DATE
      --deny-maintenance-period-start-date=DENY_MAINTENANCE_PERIOD_START_DATE --deny-maintenance-period-time=DENY_MAINTENANCE_PERIOD_TIME]
    [--egress-enabled
      --egress-fqdns=[EGRESS_FQDNS,...] --marketplace-enabled]
    [--maintenance-window-day=MAINTENANCE_WINDOW_DAY
      --maintenance-window-time=MAINTENANCE_WINDOW_TIME]
    [--oauth-client-id=OAUTH_CLIENT_ID
      --oauth-client-secret=OAUTH_CLIENT_SECRET] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Looker instance
you want to update. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Looker region of the instance. Overrides the default
     looker/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property looker/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-email-domains` | [ALLOWED_EMAIL_DOMAINS,...] |  | _[which your users can deliver Looker (Google Cloud core) content.]_ This specifies the entire allowed email domain list. |
| `--async` |  |  | _[which your users can deliver Looker (Google Cloud core) content.]_ Return immediately, without waiting for the operation in progress to complete. |
| `--class-type` | one of: p1, r1 |  | _[which your users can deliver Looker (Google Cloud core) content.]_ The class type of the Looker instance. CLASS_TYPE must be one of: p1, r1. |
| `--custom-domain` | CUSTOM_DOMAIN |  | _[registrar for your custom domain to work properly.]_ Domain name wanted to serve the Looker instance. |
| `--linked-lsp-project-number` | LINKED_LSP_PROJECT_NUMBER |  | _[registrar for your custom domain to work properly.]_ The Looker Studio Pro project number to be linked. |
| `--public-ip-enabled` |  |  | _[registrar for your custom domain to work properly.]_ This specifies whether public IP is enabled on the Looker instance. |
| `--add-developer-users` | ADD_DEVELOPER_USERS |  | _[up to 50 total users, distributed across Viewer, Standard, and Developer.]_ Number of additional Developer Users to allocate to the Looker Instance. |
| `--add-standard-users` | ADD_STANDARD_USERS |  | _[up to 50 total users, distributed across Viewer, Standard, and Developer.]_ Number of additional Standard Users to allocate to the Looker Instance. |
| `--add-viewer-users` | ADD_VIEWER_USERS |  | _[up to 50 total users, distributed across Viewer, Standard, and Developer.]_ Number of additional Viewer Users to allocate to the Looker Instance. |
| `--clear-periodic-export-config` |  |  | _[At most one of these can be specified:]_ Clears all periodic export configuration from the instance. |
| `--deny-maintenance-period-end-date` | DENY_MAINTENANCE_PERIOD_END_DATE |  | _[90-days.]_ End date of the deny maintenance period in format: YYYY-MM-DD This flag argument must be specified if any of the other arguments in this group are specified. |
| `--deny-maintenance-period-start-date` | DENY_MAINTENANCE_PERIOD_START_DATE |  | _[90-days.]_ Start date of the deny maintenance period in format: YYYY-MM-DD This flag argument must be specified if any of the other arguments in this group are specified. |
| `--deny-maintenance-period-time` | DENY_MAINTENANCE_PERIOD_TIME |  | _[90-days.]_ Time in UTC when the period starts and ends. A valid time of day must be specified in 24hr format (ex: 13:00, 17:30, 23:45). This flag argument must be specified if any of the other arguments in this group are specified. |
| `--egress-enabled` |  |  | _[Looker (Google Cloud core) instance to a third party service provider.]_ This specifies whether controlled egress is enabled on the Looker instance. To disable controlled egress, use the --no-egress-enabled flag. |
| `--egress-fqdns` | [EGRESS_FQDNS,...] |  | _[Looker (Google Cloud core) instance to a third party service provider.]_ List of FQDNs that are allowed to egress from the Looker instance. Example: --egress-fqdns="github.com,my.salesforce.com". To clear all egress FQDNs, use --egress-fqdns="". |
| `--marketplace-enabled` |  |  | _[Looker (Google Cloud core) instance to a third party service provider.]_ This specifies whether marketplace is enabled for controlled egress on the Looker instance. To disable marketplace for controlled egress, use the --no-marketplace-enabled flag. |
| `--maintenance-window-day` | one of: friday, monday, saturday, sunday, thursday, tuesday, wednesday |  | _[which disrupts service briefly.]_ Day of the week for the maintenance window, in UTC time zone. MAINTENANCE_WINDOW_DAY must be one of: friday, monday, saturday, sunday, thursday, tuesday, wednesday. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--maintenance-window-time` | MAINTENANCE_WINDOW_TIME |  | _[which disrupts service briefly.]_ Hour of day for maintenance window, in UTC time zone. A valid time of day must be specified in 24hr format (ex: 13:00, 17:30, 23:45). Maintenance will be scheduled within 60 minutes. To set the maintenance-window-time attribute: + provide the argument --maintenance-window-time on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--oauth-client-id` | OAUTH_CLIENT_ID |  | _[https://developers.google.com/identity/protocols/oauth2/web-server#creatingcred]_ The client ID from an external OAuth application. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--oauth-client-secret` | OAUTH_CLIENT_SECRET |  | _[https://developers.google.com/identity/protocols/oauth2/web-server#creatingcred]_ The client secret from an external OAuth application. This flag argument must be specified if any of the other arguments in this group are specified. |


**Examples:**
```bash
To update the maintenance window to Sunday at 11:00 PM for a Looker
instance with the name my-looker-instance, run:

    $ gcloud looker instances update my-looker-instance \
        --maintenance-window-day=sunday \
        --maintenance-window-time='23:00' --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/instances/update)

---