# gcloud colab runtimes

manage Colab Enterprise runtimes

### `gcloud colab runtimes create`

Create a notebook runtime

Create a notebook runtime that can be used to run code from your notebook
(IPYNB file).

**Synopsis:**
```
gcloud colab runtimes create --display-name=DISPLAY_NAME
    --runtime-template=RUNTIME_TEMPLATE [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--region=REGION] [--runtime-id=RUNTIME_ID]
    [--runtime-user=RUNTIME_USER] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | The display name of the runtime to create. |
| `--runtime-template-id` |  |  | _[configure the runtime with. This was optionally provided by setting]_ |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description |
| `--labels` | [KEY=VALUE,...] |  | Add labels to identify and group the runtime template. |
| `--runtime-id` | RUNTIME_ID |  | _[+ set the property colab/region.]_ The id of the runtime to create. If not specified, a random id will be generated. |
| `--runtime-user` | RUNTIME_USER |  | _[+ set the property colab/region.]_ User email for the runtime owner. Runtimes can only be used by the owner. If a user is not provided, the gcloud user will be assumed to be the owner. The user cannot be a service account. |


**Examples:**
```bash
To create a runtime in region 'us-central1' with the display name
'my-runtime' and template with id 'my-template', run:

    $ gcloud colab runtimes create --region=us-central1 \
        --display-name=my-runtime --runtime-template=my-template

To create a runtime for user 'USER@DOMAIN.COM', run:

    $ gcloud colab runtimes create --runtime-user=USER@DOMAIN.COM \
        --region=us-central1 --display-name=my-runtime \
        --runtime-template=my-template
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtimes/create)

---
### `gcloud colab runtimes delete`

Delete a runtime

Delete a Colab Enterprise notebook runtime.

**Synopsis:**
```
gcloud colab runtimes delete (RUNTIME : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime resource - Unique name of the runtime to delete. This was
optionally provided by setting --runtime-id in the create runtime command,
or was system-generated if unspecified. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument runtime on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME
     ID of the runtime or fully qualified identifier for the runtime.

     To set the name attribute:
     + provide the argument runtime on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the runtime.

     To set the region attribute:
     + provide the argument runtime on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a runtime with id 'my-runtime' in region 'us-central1', run:

    $ gcloud colab runtimes delete my-runtime --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtimes/delete)

---
### `gcloud colab runtimes describe`

Describe a runtime

Describe a Colab Enterprise notebook runtime.

**Synopsis:**
```
gcloud colab runtimes describe (RUNTIME : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime resource - Unique name of the runtime to describe. This was
optionally provided by setting --runtime-id in the create runtime command,
or was system-generated if unspecified. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument runtime on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME
     ID of the runtime or fully qualified identifier for the runtime.

     To set the name attribute:
     + provide the argument runtime on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the runtime.

     To set the region attribute:
     + provide the argument runtime on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Examples:**
```bash
To describe a runtime with id 'my-runtime' in region 'us-central1', run:

    $ gcloud colab runtimes describe my-runtime --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtimes/describe)

---
### `gcloud colab runtimes list`

List your project's runtimes

List your project's Colab Enterprise notebook runtimes in a given region.

**Synopsis:**
```
gcloud colab runtimes list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property colab/region. |


**Examples:**
```bash
To list your runtimes in region 'us-central1', run:

    $ gcloud colab runtimes list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtimes/list)

---
### `gcloud colab runtimes start`

Start a stopped runtime

Start a stopped Colab Enterprise notebook runtime.

**Synopsis:**
```
gcloud colab runtimes start (RUNTIME : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime resource - Unique name of the runtime to start. This was
optionally provided by setting --runtime-id in the create runtime command,
or was system-generated if unspecified. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument runtime on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME
     ID of the runtime or fully qualified identifier for the runtime.

     To set the name attribute:
     + provide the argument runtime on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the runtime.

     To set the region attribute:
     + provide the argument runtime on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To start a runtime with id 'my-runtime' in region 'us-central1', run:

    $ gcloud colab runtimes start my-runtime --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtimes/start)

---
### `gcloud colab runtimes stop`

Stop a runtime

Stop a Colab Enterprise notebook runtime.

**Synopsis:**
```
gcloud colab runtimes stop (RUNTIME : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime resource - Unique name of the runtime to stop. This was optionally
provided by setting --runtime-id in the create runtime command, or was
system-generated if unspecified. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument runtime on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME
     ID of the runtime or fully qualified identifier for the runtime.

     To set the name attribute:
     + provide the argument runtime on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the runtime.

     To set the region attribute:
     + provide the argument runtime on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To stop a runtime with id my-runtime in region us-central1, run:

    $ gcloud colab runtimes stop my-runtime --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtimes/stop)

---
### `gcloud colab runtimes upgrade`

Upgrade a runtime

Upgrade a Colab Enterprise notebook runtime.

**Synopsis:**
```
gcloud colab runtimes upgrade (RUNTIME : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime resource - Unique name of the runtime to upgrade. This was
optionally provided by setting --runtime-id in the create runtime command,
or was system-generated if unspecified. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument runtime on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME
     ID of the runtime or fully qualified identifier for the runtime.

     To set the name attribute:
     + provide the argument runtime on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the runtime.

     To set the region attribute:
     + provide the argument runtime on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To upgrade a runtime with id 'my-runtime' in region 'us-central1', run:

    $ gcloud colab runtimes upgrade my-runtime --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtimes/upgrade)

---