# gcloud ai persistent-resources

create and manage Vertex AI persistent resources

### `gcloud ai persistent-resources create`

Create a new persistent resource

This command will create a persistent resource on the users project to use
with Vertex AI custom training jobs. Persistent resources remain active
until they are deleted by the user.

**Synopsis:**
```
gcloud ai persistent-resources create
    --persistent-resource-id=PERSISTENT_RESOURCE_ID
    (--config=CONFIG --resource-pool-spec=[RESOURCE_POOL_SPEC,...])
    [--display-name=DISPLAY_NAME] [--enable-custom-service-account]
    [--labels=[KEY=VALUE,...]] [--network=NETWORK] [--region=REGION]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--persistent-resource-id` | PERSISTENT_RESOURCE_ID |  | User-specified ID of the Persistent Resource. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Display name of the Persistent Resource. |
| `--enable-custom-service-account` |  |  | Whether or not to use a custom user-managed service account with this Persistent Resource. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--network` | NETWORK |  | Full name of the Google Compute Engine network to which the Job is peered with. Private services access must already have been configured. If unspecified, the Job is not peered with any network. |


**Examples:**
```bash
To create a PersistentResource under project example in region us-central1,
run:

    $ gcloud ai persistent-resources create --region=us-central1 \
        --project=example \
        --resource-pool-spec=replica-count=1,\
    machine-type='n1-standard-4' --display-name=example-resource
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/persistent-resources/create)

---
### `gcloud ai persistent-resources delete`

Delete an active Persistent Resource

If the Persistent Resource is not in the active state, the command will not
perform any operation.

**Synopsis:**
```
gcloud ai persistent-resources delete
    (PERSISTENT_RESOURCE : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Persistent resource resource - The persistent resource to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument persistent_resource on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PERSISTENT_RESOURCE
     ID of the persistent resource or fully qualified identifier for the
     persistent resource.

     To set the name attribute:
     + provide the argument persistent_resource on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the persistent resource.

     To set the region attribute:
     + provide the argument persistent_resource on the command line with
       a fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To delete a persistent resource 123 under project example in region
us-central1, run:

    $ gcloud ai persistent-resources delete 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/persistent-resources/delete)

---
### `gcloud ai persistent-resources describe`

Get detailed information about a PersistentResource with a given id

**Synopsis:**
```
gcloud ai persistent-resources describe
    (PERSISTENT_RESOURCE : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Persistent resource resource - The persistent resource to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument persistent_resource on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PERSISTENT_RESOURCE
     ID of the persistent resource or fully qualified identifier for the
     persistent resource.

     To set the name attribute:
     + provide the argument persistent_resource on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the persistent resource.

     To set the region attribute:
     + provide the argument persistent_resource on the command line with
       a fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To get the persistent resource with the PersistentResource id 123 under
project example in region us-central1, run:

    $ gcloud ai persistent-resources describe 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/persistent-resources/describe)

---
### `gcloud ai persistent-resources list`

Lists the active persistent resources

**Synopsis:**
```
gcloud ai persistent-resources list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property ai/region; + choose one from the prompted list of available regions. |


**Examples:**
```bash
To list the persistent resources of project example in region us-central1,
run:

    $ gcloud ai persistent-resources list --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/persistent-resources/list)

---
### `gcloud ai persistent-resources reboot`

Reboot a Persistent Resource

**Synopsis:**
```
gcloud ai persistent-resources reboot
    (PERSISTENT_RESOURCE : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Persistent resource resource - The persistent resource to reboot. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument persistent_resource on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PERSISTENT_RESOURCE
     ID of the persistent resource or fully qualified identifier for the
     persistent resource.

     To set the name attribute:
     + provide the argument persistent_resource on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the persistent resource.

     To set the region attribute:
     + provide the argument persistent_resource on the command line with
       a fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To reboot a persistent resource 123 under project example in region
us-central1, run:

    $ gcloud ai persistent-resources reboot 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/persistent-resources/reboot)

---