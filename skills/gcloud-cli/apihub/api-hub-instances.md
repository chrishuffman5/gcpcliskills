# gcloud apihub api-hub-instances

manage Api Hub Instance resources

### `gcloud apihub api-hub-instances create`

Create an Api Hub Instance

Create an api hub instance.

**Synopsis:**
```
gcloud apihub api-hub-instances create
    (API_HUB_INSTANCE : --location=LOCATION)
    (--config-cmek-key-name=CONFIG_CMEK_KEY_NAME
      --config-disable-search
      --config-encryption-type=CONFIG_ENCRYPTION_TYPE
      --config-vertex-location=CONFIG_VERTEX_LOCATION)
    [--async] [--description=DESCRIPTION] [--labels=[LABELS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ApiHubInstance resource - Identifier. Format:
projects/{project}/locations/{location}/apiHubInstances/{apiHubInstance}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument api_hub_instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  API_HUB_INSTANCE
     ID of the apiHubInstance or fully qualified identifier for the
     apiHubInstance.

     To set the api_hub_instance attribute:
     + provide the argument api_hub_instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the apiHubInstance resource.

     To set the location attribute:
     + provide the argument api_hub_instance on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config-cmek-key-name` | CONFIG_CMEK_KEY_NAME |  | _[Available configurations to provision an ApiHub Instance. At least one of these must be specified:]_ The Customer Managed Encryption Key (CMEK) used for data encryption. The CMEK name should follow the format of projects/([^/]+)/locations/([^/]+)/keyRings/([^/]+)/cryptoKeys/([^/]+), where the location must match the instance location. If the CMEK is not provided, a GMEK will be created for the instance. |
| `--config-disable-search` |  | false | _[At least one of these must be specified:]_ If true, the search will be disabled for the instance. The default value is false. |
| `--config-encryption-type` | CONFIG_ENCRYPTION_TYPE |  | _[At least one of these must be specified:]_ Encryption type for the region. If the encryption type is CMEK, the cmek_key_name must be provided. If no encryption type is provided, GMEK will be used. CHOICES: cmek (encryption using customer managed encryption key), gmek (default encryption using Google managed encryption key). |
| `--config-vertex-location` | CONFIG_VERTEX_LOCATION |  | _[At least one of these must be specified:]_ The name of the Vertex AI location where the data store is stored. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the ApiHub instance. |
| `--labels` | [LABELS,...] |  | Instance labels to represent user-provided metadata. Refer to cloud documentation on labels for more details. |

**Examples:**
```bash
To create an API Hub instance, run:

    $ gcloud apihub api-hub-instances create --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/api-hub-instances/create)

---
### `gcloud apihub api-hub-instances delete`

Delete an Api Hub Instance

Delete an api hub instance.

**Synopsis:**
```
gcloud apihub api-hub-instances delete
    (API_HUB_INSTANCE : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ApiHubInstance resource - The name of the Api Hub instance to delete.
Format:
projects/{project}/locations/{location}/apiHubInstances/{apiHubInstance}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument api_hub_instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  API_HUB_INSTANCE
     ID of the apiHubInstance or fully qualified identifier for the
     apiHubInstance.

     To set the api_hub_instance attribute:
     + provide the argument api_hub_instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the apiHubInstance resource.

     To set the location attribute:
     + provide the argument api_hub_instance on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |

**Examples:**
```bash
To delete the API Hub instance in project my-project and location
us-central1, run:

    $ gcloud apihub api-hub-instances delete --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/api-hub-instances/delete)

---
### `gcloud apihub api-hub-instances describe`

Describe an Api Hub Instance

Describe an api hub instance.

**Synopsis:**
```
gcloud apihub api-hub-instances describe
    (API_HUB_INSTANCE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ApiHubInstance resource - The name of the Api Hub instance to retrieve.
Format:
projects/{project}/locations/{location}/apiHubInstances/{apiHubInstance}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument api_hub_instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  API_HUB_INSTANCE
     ID of the apiHubInstance or fully qualified identifier for the
     apiHubInstance.

     To set the api_hub_instance attribute:
     + provide the argument api_hub_instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the apiHubInstance resource.

     To set the location attribute:
     + provide the argument api_hub_instance on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the API Hub instance in project my-project and location
us-central1, run:

    $ gcloud apihub api-hub-instances describe --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/api-hub-instances/describe)

---
### `gcloud apihub api-hub-instances lookup`

Lookup apiHubInstances

Lookup apiHubInstances.

**Synopsis:**
```
gcloud apihub api-hub-instances lookup --location=LOCATION
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ Location resource - There will always be only one Api Hub instance for a Google Cloud project across all locations. The parent resource for the Api Hub instance resource. Format: projects/{project}/locations/{location}. ID of the location or fully qualified identifier for the location. To set the location attribute: provide the argument --location on the command line. To set the project attribute: provide the argument --location on the command line with a fully specified name; provide the argument --project on the command line; set the property core/project. |

**Examples:**
```bash
To lookup all apiHubInstances, run:

    $ gcloud apihub api-hub-instances lookup
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/api-hub-instances/lookup)

---
