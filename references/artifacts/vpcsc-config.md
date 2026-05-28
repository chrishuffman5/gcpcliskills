# gcloud artifacts vpcsc-config

manage Artifact Registry VPC Service Controls configuration for remote repositories

### `gcloud artifacts vpcsc-config allow`

Allow Artifact Registry remote repositories inside a service perimeter to retrieve data from their upstream sources outside of the perimeter

Allow Artifact Registry remote repositories inside a service perimeter to
retrieve data from their upstream sources outside of the perimeter.

This command can fail for the following reasons:
  o Lack of permission - "accesscontextmanager.policies.update".
  o The resource could be outside of the VPC SC perimeter.
  o Lack of permission - "artifactregistry.vpcscconfigs.update"

**Synopsis:**
```
gcloud artifacts vpcsc-config allow [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property artifacts/location. |


**Examples:**
```bash
The following command allows remote repositories in the project my-project
and in the region us--west1 to retrieve data from upstream sources outside
the perimeter:

    $ gcloud artifacts vpcsc-config allow --project=my-project \
       --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/vpcsc-config/allow)

---
### `gcloud artifacts vpcsc-config deny`

Deny access to upstream sources outside the service perimeter for Artifact Registry remote repositories inside the perimeter

Deny access to upstream sources outside the service perimeter for Artifact
Registry remote repositories inside the perimeter.

This command can fail for the following reasons:
  o Lack of permission - "accesscontextmanager.policies.update".
  o The resource could be outside of the VPC SC perimeter.
  o Lack of permission - "artifactregistry.vpcscconfigs.update"

**Synopsis:**
```
gcloud artifacts vpcsc-config deny [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property artifacts/location. |


**Examples:**
```bash
The following command denies access to upstream sources outside the service
perimeter for remote repositories in the project my-project and in the
region us--west1:

    $ gcloud artifacts vpcsc-config deny --project=my-project \
       --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/vpcsc-config/deny)

---
### `gcloud artifacts vpcsc-config describe`

Describe the current Artifact Registry configuration for VPC Service Controls

Describe the current Artifact Registry configuration for VPC Service
Controls.

This command can fail for the following reasons:
  o Lack of permission - "accesscontextmanager.policies.get".
  o The resource could be outside of the VPC SC perimeter.
  o Lack of permission - "artifactregistry.vpcscconfigs.get"

**Synopsis:**
```
gcloud artifacts vpcsc-config describe [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property artifacts/location. |


**Examples:**
```bash
The following command returns the current VPC Service Controls
configuration for the project my-project and region us-west1:

    $ gcloud artifacts vpcsc-config describe --project=my-project \
       --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/vpcsc-config/describe)

---