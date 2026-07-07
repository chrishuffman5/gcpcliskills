# gcloud deploy (top-level commands)

### `gcloud deploy apply`

Applies a yaml configuration containing Delivery Pipeline(s), Target(s), Custom Target Type(s), Deploy Policy(ies), and Automation(s) declarative definitions

Applies a yaml configuration containing Delivery Pipeline(s), Target(s),
Custom Target Type(s), Deploy Policy(ies), and Automation(s) declarative
definitions.

**Synopsis:**
```
gcloud deploy apply --file=FILE [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file` | FILE |  | Path to yaml file containing Delivery Pipeline(s), Target(s) declarative definitions. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the region attribute: + provide the argument --region on the command line; + set the property deploy/region. |


**Examples:**
```bash
To apply a Cloud Deploy YAML file deploy.yaml:

    $ gcloud deploy apply --file=deploy.yaml --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/apply)

---
### `gcloud deploy delete`

Deletes Delivery Pipeline(s), Target(s), Custom Target Type(s), and Automation(s) in a yaml configuration

Deletes Delivery Pipeline(s), Target(s), Custom Target Type(s), and
Automation(s) in a yaml configuration.

**Synopsis:**
```
gcloud deploy delete --file=FILE [--force] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file` | FILE |  | Path to yaml file containing Delivery Pipeline(s), Target(s) declarative definitions. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | If true, the delivery pipeline and its sub-resources (releases and rollouts) are deleted. |


**Examples:**
```bash
To delete the resources in a Cloud Deploy YAML file deploy.yaml:

    $ gcloud deploy delete --file=deploy.yaml --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/delete)

---
### `gcloud deploy get-config`

Get the Cloud Deploy config for the provided region and project

Get the Cloud Deploy config for the provided region and project.

**Synopsis:**
```
gcloud deploy get-config [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the region attribute: + provide the argument --region on the command line; + set the property deploy/region. |


**Examples:**
```bash
To get the config for project test-project in region us-central1:

    $ gcloud deploy get-config --project=test-project \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/get-config)

---