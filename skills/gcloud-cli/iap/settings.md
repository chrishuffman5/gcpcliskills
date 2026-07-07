# gcloud iap settings

manage IAP settings

### `gcloud iap settings get`

Get the setting for an IAP resource

Get the setting for an IAP resource.

**Synopsis:**
```
gcloud iap settings get
    [--folder=FOLDER --organization=ORGANIZATION --project=PROJECT
      --region=REGION
      --resource-type=RESOURCE_TYPE --service=SERVICE --version=VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | Folder ID. |
| `--organization` | ORGANIZATION |  | Organization ID. |
| `--project` | PROJECT |  | Project ID. |
| `--region` | REGION |  | Region name. Not applicable for app-engine. Required when resource-type=compute and regional scoped. Not applicable for global scoped compute. |
| `--resource-type` | one of: app-engine, iap_web, compute, organization, folder, backend-services, forwarding-rule |  | Resource type of the IAP resource. For Backend Services, you can use both compute and backend-services as resource type. RESOURCE_TYPE must be one of: app-engine, iap_web, compute, organization, folder, backend-services, forwarding-rule. |
| `--service` | SERVICE |  | Service name. Optional when resource-type is compute or app-engine. |
| `--version` | VERSION |  | Version name. Not applicable for compute. Optional when resource-type=app-engine. |


**Examples:**
```bash
To get the IAP setting for the resources within an organization, run:

    $ gcloud iap settings get --organization=ORGANIZATION_ID

To get the IAP setting for the resources within a folder, run:

    $ gcloud iap settings get --folder=FOLDER_ID

To get the IAP setting for the resources within a project, run:

    $ gcloud iap settings get --project=PROJECT_ID

To get the IAP setting for web type resources within a project, run:

    $ gcloud iap settings get --project=PROJECT_ID \
        --resource-type=iap_web

To get the IAP setting for all app engine services within a project, run:

    $ gcloud iap settings get --project=PROJECT_ID \
        --resource-type=app-engine

To get the IAP setting for an app engine service within a project, run:

    $ gcloud iap settings get --project=PROJECT_ID \
        --resource-type=app-engine --service=SERVICE_ID

To get the IAP setting for an app engine service version within a project,
run:

    $ gcloud iap settings get --project=PROJECT_ID \
        --resource-type=app-engine --service=SERVICE_ID \
        --version=VERSION_ID

To get the IAP setting for all backend services within a project, run:

    $ gcloud iap settings get --project=PROJECT_ID \
        --resource-type=backend-services

To get the IAP setting for a backend service within a project, run:

    $ gcloud iap settings get --project=PROJECT_ID \
        --resource-type=backend-services --service=SERVICE_ID

To get the IAP setting for a regional backend service within a project,
run:

    $ gcloud iap settings get --project=PROJECT_ID \
        --resource-type=backend-services --service=SERVICE_ID \
        --region=REGION_ID

To get the IAP setting for all forwarding rules within a project, run:

    $ gcloud iap settings get --project=PROJECT_ID \
        --resource-type=forwarding-rule

To get the IAP setting for a forwarding rule within a project, run:

    $ gcloud iap settings get --project=PROJECT_ID \
        --resource-type=forwarding-rule --service=SERVICE_ID

To get the IAP setting for a regional forwarding rule within a project,
run:

    $ gcloud iap settings get --project=PROJECT_ID \
        --resource-type=forwarding-rule --service=SERVICE_ID \
        --region=REGION_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/settings/get)

---
### `gcloud iap settings set`

Set the setting for an IAP resource

Set the setting for an IAP resource.

**Synopsis:**
```
gcloud iap settings set SETTING_FILE
    [--folder=FOLDER --organization=ORGANIZATION --project=PROJECT
      --region=REGION
      --resource-type=RESOURCE_TYPE --service=SERVICE --version=VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SETTING_FILE
   JSON or YAML file containing the IAP resource settings.

   JSON example:

       {
         "access_settings": {
           "oauth_settings": {
             "login_hint": {
               "value": "test_hint"
             }
           },
           "gcip_settings": {
             "tenant_ids": [
               "tenant1-p9puj",
               "tenant2-y8rxc"
             ],
             "login_page_uri": {
               "value": "https://test.com/?apiKey=abcd_efgh"
             }
           },
           "cors_settings": {
             "allow_http_options": {
               "value": true
             }
           }
         },
         "application_settings": {
           "csm_settings": {
             "rctoken_aud": {
               "value": "test_aud"
             }
           }
         }
       }

   YAML example:

       accessSettings :
         oauthSettings:
           loginHint: test_hint
         gcipSettings:
           tenantIds:
           - tenant1-p9puj
           - tenant2-y8rxc
           loginPageUri: https://test.com/?apiKey=abcd_efgh
         corsSettings:
           allowHttpOptions: true
       applicationSettings:
         csmSettings:
           rctokenAud: test_aud
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | Folder ID. |
| `--organization` | ORGANIZATION |  | Organization ID. |
| `--project` | PROJECT |  | Project ID. |
| `--region` | REGION |  | Region name. Not applicable for app-engine. Required when resource-type=compute and regional scoped. Not applicable for global scoped compute. |
| `--resource-type` | one of: app-engine, iap_web, compute, organization, folder, backend-services, forwarding-rule |  | Resource type of the IAP resource. For Backend Services, you can use both compute and backend-services as resource type. RESOURCE_TYPE must be one of: app-engine, iap_web, compute, organization, folder, backend-services, forwarding-rule. |
| `--service` | SERVICE |  | Service name. Optional when resource-type is compute or app-engine. |
| `--version` | VERSION |  | Version name. Not applicable for compute. Optional when resource-type=app-engine. |


**Examples:**
```bash
To set the IAP setting for the resources within an organization, run:

    $ gcloud iap settings set iap_settings.yaml \
        --organization=ORGANIZATION_ID

To set the IAP setting for the resources within a folder, run:

    $ gcloud iap settings set iap_settings.yaml --folder=FOLDER_ID

To set the IAP setting for the resources within a project, run:

    $ gcloud iap settings set iap_settings.yaml --project=PROJECT_ID

To set the IAP setting for web type resources within a project, run:

    $ gcloud iap settings set iap_settings.yaml --project=PROJECT_ID \
        --resource-type=iap_web

To set the IAP setting for all app engine services within a project, run:

    $ gcloud iap settings set iap_settings.yaml --project=PROJECT_ID \
        --resource-type=app-engine

To set the IAP setting for an app engine service within a project, run:

    $ gcloud iap settings set iap_settings.yaml --project=PROJECT_ID \
        --resource-type=app-engine --service=SERVICE_ID

To set the IAP setting for an app engine service version within a project,
run:

    $ gcloud iap settings set iap_settings.yaml --project=PROJECT_ID \
        --resource-type=app-engine --service=SERVICE_ID \
        --version=VERSION_ID

To set the IAP setting for all backend services within a project, run:

    $ gcloud iap settings set iap_settings.yaml --project=PROJECT_ID \
        --resource-type=backend-services

To set the IAP setting for a backend service within a project, run:

    $ gcloud iap settings set iap_settings.yaml --project=PROJECT_ID \
        --resource-type=backend-services --service=SERVICE_ID

To set the IAP setting for a region backend service within a project, run:

    $ gcloud iap settings set iap_settings.yaml --project=PROJECT_ID \
        --resource-type=backend-services --service=SERVICE_ID \
        --region=REGION_ID

To set the IAP setting for all forwarding rule within a project, run:

    $ gcloud iap settings set iap_settings.yaml --project=PROJECT_ID \
        --resource-type=forwarding-rule

To set the IAP setting for a forwarding rule within a project, run:

    $ gcloud iap settings set iap_settings.yaml --project=PROJECT_ID \
        --resource-type=forwarding-rule --service=SERVICE_ID

To set the IAP setting for a region forwarding rule within a project, run:

    $ gcloud iap settings set iap_settings.yaml --project=PROJECT_ID \
        --resource-type=forwarding-rule --service=SERVICE_ID \
        --region=REGION_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/settings/set)

---