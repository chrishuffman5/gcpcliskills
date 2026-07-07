# gcloud compute preview-features

read and manipulate Compute Engine Preview Features

### `gcloud compute preview-features describe`

Describe a preview feature

Describe a preview feature.

**Synopsis:**
```
gcloud compute preview-features describe PREVIEW_FEATURE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Preview feature resource - Name of the preview feature you want to
inspect. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument preview_feature on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PREVIEW_FEATURE
     ID of the preview feature or fully qualified identifier for the
     preview feature.

     To set the preview_feature attribute:
     + provide the argument preview_feature on the command line.
```

**Examples:**
```bash
To retrieve a single preview feature and print its properties, run the
following command:

    $ gcloud compute preview-features describe my-preview-feature
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/preview-features/describe)

---
### `gcloud compute preview-features list`

View preview features

View preview features.

**Synopsis:**
```
gcloud compute preview-features list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To display all preview features, run the following command:

    $ gcloud compute preview-features list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/preview-features/list)

---
### `gcloud compute preview-features update`

Update a preview feature's activation status

Update a preview feature's activation status.

**Synopsis:**
```
gcloud compute preview-features update PREVIEW_FEATURE
    --activation-status=ACTIVATION_STATUS
    (--custom-rollout-plan=CUSTOM_ROLLOUT_PLAN
      | --rollout-plan=ROLLOUT_PLAN) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Preview feature resource - Name of the preview feature you want to update.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument preview_feature on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PREVIEW_FEATURE
     ID of the preview feature or fully qualified identifier for the
     preview feature.

     To set the preview_feature attribute:
     + provide the argument preview_feature on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--activation-status` | one of: enabled, unspecified |  | The activation status of the preview feature. ACTIVATION_STATUS must be one of: enabled, unspecified. |


**Examples:**
```bash
To enable/unspecify a preview feature's activation status, run the
following command:

    $ gcloud compute preview-features update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/preview-features/update)

---