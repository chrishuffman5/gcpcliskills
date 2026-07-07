# gcloud iap oauth-brands

manage IAP OAuth brands

### `gcloud iap oauth-brands create`

Create a Cloud OAuth brand for the project

(DEPRECATED) This command is deprecated and will be non-functional after
the IAP OAuth Admin APIs are turned down. Jan 19, 2026: Google will
discontinue support for the IAP OAuth Admin APIs. New projects will not be
able to use these APIs. March 19, 2026: The IAP OAuth Admin APIs will be
permanently shut down. Access to this feature will no longer be available.

gcloud iap oauth-brands create is used to create a Cloud OAuth brand for
the project. The brand is 'internal only', meaning OAuth clients created
under it only accept requests from users who belong to the same G Suite
account as the project. The brand is created in unreviewed status. Your
domain will not appear on the OAuth consent screen until it is reviewed
after you manually start a review process in Google Cloud Platform Console.
Note that the 'internal only' setting can be manually changed in Google
Cloud Platform Console
(https://console.cloud.google.com/apis/credentials/consent). A project can
only have one brand.

**Synopsis:**
```
gcloud iap oauth-brands create --application_title=APPLICATION_TITLE
    --support_email=SUPPORT_EMAIL [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--application` | APPLICATION_TITLE |  | Application name displayed on the OAuth consent screen. |
| `--support` | SUPPORT_EMAIL |  | Support email displayed on the OAuth consent screen. |


**Examples:**
```bash
To create a Cloud OAuth brand for the current project, run:

    $ gcloud iap oauth-brands create \
      --application_title=APPLICATION_TITLE \
      --support_email=SUPPORT_EMAIL

To create a Cloud OAuth brand for the project PROJECT_ID, run:

    $ gcloud iap oauth-brands create \
      --application_title=APPLICATION_TITLE \
      --support_email=SUPPORT_EMAIL --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/oauth-brands/create)

---
### `gcloud iap oauth-brands describe`

Describe a Cloud OAuth brand

(DEPRECATED) This command is deprecated and will be non-functional after
the IAP OAuth Admin APIs are turned down. Jan 19, 2026: Google will
discontinue support for the IAP OAuth Admin APIs. New projects will not be
able to use these APIs. March 19, 2026: The IAP OAuth Admin APIs will be
permanently shut down. Access to this feature will no longer be available.

gcloud iap oauth-brands describe is used to describe a Cloud OAuth brand.

**Synopsis:**
```
gcloud iap oauth-brands describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Brand resource - Name of the Cloud OAuth brand to describe. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument name on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the brand or fully qualified identifier for the brand.

     To set the brand attribute:
     + provide the argument name on the command line.
```

**Examples:**
```bash
To describe a Cloud OAuth brand with name NAME, run:

    $ gcloud iap oauth-brands describe NAME

To describe a Cloud OAuth brand with name NAME inside project PROJECT_ID,
run:

    $ gcloud iap oauth-brands describe NAME --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/oauth-brands/describe)

---
### `gcloud iap oauth-brands list`

List Cloud OAuth brands in the project

(DEPRECATED) This command is deprecated and will be non-functional after
the IAP OAuth Admin APIs are turned down. Jan 19, 2026: Google will
discontinue support for the IAP OAuth Admin APIs. New projects will not be
able to use these APIs. March 19, 2026: The IAP OAuth Admin APIs will be
permanently shut down. Access to this feature will no longer be available.

gcloud iap oauth-brands list is used to list the Cloud OAuth brand in the
project.

**Synopsis:**
```
gcloud iap oauth-brands list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all Cloud OAuth brands in the current project, run:

    $ gcloud iap oauth-brands list

To list all Cloud OAuth brands in the project PROJECT_ID, run:

    $ gcloud iap oauth-brands list --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/oauth-brands/list)

---