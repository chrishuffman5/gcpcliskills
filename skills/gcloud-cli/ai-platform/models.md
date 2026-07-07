# gcloud ai-platform models

AI Platform Models commands

### `gcloud ai-platform models add-iam-policy-binding`

Add IAM policy binding for a model

Add IAM policy binding to a model.

**Synopsis:**
```
gcloud ai-platform models add-iam-policy-binding MODEL --member=PRINCIPAL
    --role=ROLE [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODEL
   Name of the model.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


**Examples:**
```bash
To add an IAM policy binding for the role of roles/ml.admin for the user
test-user@gmail.com on a model with identifier my_model, run:

    $ gcloud ai-platform models add-iam-policy-binding my_model \
        --member='user:test-user@gmail.com' --role='roles/ml.admin'

To add an IAM policy binding for the role of roles/ml.admin to the service
account test-proj1@example.domain.com, run:

    $ gcloud ai-platform models add-iam-policy-binding my_model \
        --member='serviceAccount:test-proj1@example.domain.com' \
        --role='roles/ml.admin'

To add an IAM policy binding for the role of roles/ml.admin for all
authenticated users on a model with identifier my_model, run:

    $ gcloud ai-platform models add-iam-policy-binding my_model \
        --member='allAuthenticatedUsers' --role='roles/ml.admin'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and principal types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/models/add-iam-policy-binding)

---
### `gcloud ai-platform models create`

Create a new AI Platform model

Create a new AI Platform model.

**Synopsis:**
```
gcloud ai-platform models create MODEL [--description=DESCRIPTION]
    [--enable-logging] [--labels=[KEY=VALUE,...]]
    [--region=REGION | --regions=REGION,[REGION,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODEL
   Name of the model.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the model. |
| `--enable-logging` |  |  | If set, enables StackDriver Logging for online prediction. These logs are like standard server access logs, containing information such as timestamps and latency for each request. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/models/create)

---
### `gcloud ai-platform models delete`

Delete an existing AI Platform model

**Synopsis:**
```
gcloud ai-platform models delete MODEL [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODEL
   Name of the model.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


**Examples:**
```bash
To delete all models matching the regular expression vision[0-9]+, run:

    $ gcloud ai-platform models list --uri \
      --filter 'name ~ vision[0-9]+' | xargs -n 1 gcloud ai-platform \
      models delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/models/delete)

---
### `gcloud ai-platform models describe`

Describe an existing AI Platform model

Describe an existing AI Platform model.

If you would like to see all versions of a model, use gcloud ai-platform
versions list.

**Synopsis:**
```
gcloud ai-platform models describe MODEL [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODEL
   Name of the model.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/models/describe)

---
### `gcloud ai-platform models get-iam-policy`

Get the IAM policy for a model

Gets the IAM policy for the given model.

Returns an empty policy if the resource does not have a policy set.

**Synopsis:**
```
gcloud ai-platform models get-iam-policy MODEL [--region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Model resource - The AI Platform model to set IAM policy for. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument model on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MODEL
     ID of the model or fully qualified identifier for the model.

     To set the name attribute:
     + provide the argument model on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


**Examples:**
```bash
The following command gets the IAM policy for the model my_model:

    $ gcloud ai-platform models get-iam-policy my_model
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/models/get-iam-policy)

---
### `gcloud ai-platform models list`

List existing AI Platform models

List existing AI Platform models.

**Synopsis:**
```
gcloud ai-platform models list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/models/list)

---
### `gcloud ai-platform models remove-iam-policy-binding`

Remove IAM policy binding for a model

Removes a policy binding from an AI Platform Model. One binding consists of
a member, a role and an optional condition. See $ gcloud ai-platform models
get-iam-policy for examples of how to specify a model resource.

**Synopsis:**
```
gcloud ai-platform models remove-iam-policy-binding MODEL
    --member=PRINCIPAL --role=ROLE [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Model resource - The AI Platform model for which to remove IAM policy
binding from. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument model on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MODEL
     ID of the model or fully qualified identifier for the model.

     To set the name attribute:
     + provide the argument model on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


**Examples:**
```bash
To remove an IAM policy binding for the role of roles/ml.admin for the user
test-user@gmail.com on model with identifier my_model, run:

    $ gcloud ai-platform models remove-iam-policy-binding my_model \
        --member='user:test-user@gmail.com' --role='roles/ml.admin'

To remove an IAM policy binding for the role of roles/ml.admin from all
authenticated users on model my_model, run:

    $ gcloud ai-platform models remove-iam-policy-binding my_model \
        --member='allAuthenticatedUsers' --role='roles/ml.admin'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/models/remove-iam-policy-binding)

---
### `gcloud ai-platform models set-iam-policy`

Set the IAM policy for a model

Sets the IAM policy for the given model as defined in a JSON or YAML file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud ai-platform models set-iam-policy MODEL POLICY_FILE
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Model resource - The AI Platform model to set IAM policy for. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument model on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MODEL
     ID of the model or fully qualified identifier for the model.

     To set the name attribute:
     + provide the argument model on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


**Examples:**
```bash
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the model my_model:

    $ gcloud ai-platform models set-iam-policy my_model policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/models/set-iam-policy)

---
### `gcloud ai-platform models update`

Update an existing AI Platform model

Update an existing AI Platform model.

**Synopsis:**
```
gcloud ai-platform models update MODEL [--description=DESCRIPTION]
    [--region=REGION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODEL
   Name of the model.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the model. |
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/models/update)

---