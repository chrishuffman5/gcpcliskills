# gcloud notebooks runtimes

notebooks Runtimes command group

### `gcloud notebooks runtimes create`

Request for creating an runtime

Request for creating notebook runtimes.

**Synopsis:**
```
gcloud notebooks runtimes create (RUNTIME : --location=LOCATION)
    (--runtime-access-type=RUNTIME_ACCESS_TYPE
      --runtime-owner=RUNTIME_OWNER)
    (--runtime-type=RUNTIME_TYPE | [--machine-type=MACHINE_TYPE
      : --interface=INTERFACE --mode=MODE --source=SOURCE --type=TYPE])
    [--async]
    [--custom-gpu-driver-path=CUSTOM_GPU_DRIVER_PATH
      --idle-shutdown-timeout=IDLE_SHUTDOWN_TIMEOUT
      --install-gpu-driver=INSTALL_GPU_DRIVER
      --post-startup-script=POST_STARTUP_SCRIPT
      --post-startup-script-behavior=POST_STARTUP_SCRIPT_BEHAVIOR]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime resource - User-defined unique name of this runtime. The runtime
name must be 1 to 63 characters long and contain only lowercase letters,
numeric characters, and dashes. The first character must be a lowercase
letter and the last character cannot be a dash. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument runtime on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME
     ID of the runtime or fully qualified identifier for the runtime.

     To set the runtime attribute:
     + provide the argument runtime on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this runtime
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument runtime on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--runtime-access-type` | RUNTIME_ACCESS_TYPE |  | _[At least one of these must be specified:]_ access type |
| `--runtime-owner` | RUNTIME_OWNER |  | _[At least one of these must be specified:]_ runtime owner |
| `--runtime-type` | RUNTIME_TYPE |  | _[Exactly one of these must be specified:]_ runtime type |
| `--machine-type` | MACHINE_TYPE |  | _[Exactly one of these must be specified:]_ machine type This flag argument must be specified if any of the other arguments in this group are specified. |
| `--interface` | INTERFACE |  | _[Exactly one of these must be specified:]_ runtime interface |
| `--mode` | MODE |  | _[Exactly one of these must be specified:]_ runtime mode |
| `--source` | SOURCE |  | _[Exactly one of these must be specified:]_ runtime source |
| `--type` | TYPE |  | _[Exactly one of these must be specified:]_ runtime type |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--custom-gpu-driver-path` | CUSTOM_GPU_DRIVER_PATH |  | custom gpu driver path |
| `--idle-shutdown-timeout` | IDLE_SHUTDOWN_TIMEOUT |  | idle shutdown timeout |
| `--install-gpu-driver` | INSTALL_GPU_DRIVER |  | install gpu driver |
| `--post-startup-script` | POST_STARTUP_SCRIPT |  | post startup script |
| `--post-startup-script-behavior` | POST_STARTUP_SCRIPT_BEHAVIOR |  | post startup script behavior |


**Examples:**
```bash
To create a runtime, run:

    $ gcloud notebooks runtimes create example-runtime \
        --runtime-access-type=SINGLE_USER \
        --runtime-owner=example@google.com \
        --machine-type=n1-standard-4 --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/runtimes/create)

---
### `gcloud notebooks runtimes delete`

Request for deleting runtimes

Request for deleting notebook runtimes.

**Synopsis:**
```
gcloud notebooks runtimes delete (RUNTIME : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime resource - User-defined unique name of this runtime. The runtime
name must be 1 to 63 characters long and contain only lowercase letters,
numeric characters, and dashes. The first character must be a lowercase
letter and the last character cannot be a dash. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument runtime on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME
     ID of the runtime or fully qualified identifier for the runtime.

     To set the runtime attribute:
     + provide the argument runtime on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this runtime
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument runtime on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a runtime, run:

    $ gcloud notebooks runtimes delete example-runtime \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/runtimes/delete)

---
### `gcloud notebooks runtimes describe`

Request for describing runtimes

Request for describing notebook runtimes.

**Synopsis:**
```
gcloud notebooks runtimes describe (RUNTIME : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime resource - User-defined unique name of this runtime. The runtime
name must be 1 to 63 characters long and contain only lowercase letters,
numeric characters, and dashes. The first character must be a lowercase
letter and the last character cannot be a dash. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument runtime on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME
     ID of the runtime or fully qualified identifier for the runtime.

     To set the runtime attribute:
     + provide the argument runtime on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this runtime
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument runtime on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Examples:**
```bash
To describe a runtime, run:

    $ gcloud notebooks runtimes describe example-runtime \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/runtimes/describe)

---
### `gcloud notebooks runtimes diagnose`

Request for diagnose runtimes

Request for diagnose notebook runtimes.

**Synopsis:**
```
gcloud notebooks runtimes diagnose (RUNTIME : --location=LOCATION)
    --gcs-bucket=GCS_BUCKET [--async] [--enable-copy-home-files]
    [--enable-packet-capture] [--enable-repair]
    [--relative-path=RELATIVE_PATH] [--timeout-minutes=TIMEOUT_MINUTES]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime resource - User-defined unique name of this runtime. The runtime
name must be 1 to 63 characters long and contain only lowercase letters,
numeric characters, and dashes. The first character must be a lowercase
letter and the last character cannot be a dash. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument runtime on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME
     ID of the runtime or fully qualified identifier for the runtime.

     To set the runtime attribute:
     + provide the argument runtime on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this runtime
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument runtime on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-bucket` | GCS_BUCKET |  | The Cloud Storage bucket where the log files generated from the diagnose command will be stored. storage.buckets.writer permissions must be given to project's service account or user credential. Format: gs://{gcs_bucket} |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--enable-copy-home-files` |  |  | Enables flag to copy all /home/jupyter folder contents |
| `--enable-packet-capture` |  |  | Enables flag to capture packets from the runtime for 30 seconds |
| `--enable-repair` |  |  | Enables flag to repair service for runtime |
| `--relative-path` | RELATIVE_PATH |  | Defines the relative storage path in the Cloud Storage bucket where the diagnostic logs will be written. Default path will be the root directory of the Cloud Storage bucketFormat of full path: gs://{gcs_bucket}/{relative_path}/ |
| `--timeout-minutes` | TIMEOUT_MINUTES |  | Maximum amount of time in minutes before the operation times out |


**Examples:**
```bash
To diagnose an runtime, run:

    $ gcloud notebooks runtimes diagnose example-runtime \
      --location=us-central1 --gcs-bucket=gs://example-bucket

To diagnose an runtime with a relative path:

    $ gcloud notebooks runtimes diagnose example-runtime \
      --location=us-central1 --gcs-bucket=gs://example-bucket \
      --relative-path=logs

To diagnose an runtime, with packet capture:

    $ gcloud notebooks runtimes diagnose example-runtime \
      --location=us-central1 --gcs-bucket=gs://example-bucket \
      --enable-packet-capture
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/runtimes/diagnose)

---
### `gcloud notebooks runtimes list`

Request for listing runtimes

Request for listing runtimes.

**Synopsis:**
```
gcloud notebooks runtimes list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property notebooks/location. |


**Examples:**
```bash
To list runtimes in a particular location, run:

    $ gcloud notebooks runtimes list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/runtimes/list)

---
### `gcloud notebooks runtimes migrate`

Request for migrating runtimes

Request for migrating notebook runtimes.

**Synopsis:**
```
gcloud notebooks runtimes migrate (RUNTIME : --location=LOCATION) [--async]
    [--post-startup-script-option=POST_STARTUP_SCRIPT_OPTION;
      default="POST_STARTUP_SCRIPT_OPTION_UNSPECIFIED"]
    [--service-account=SERVICE_ACCOUNT]
    [--network=NETWORK [--subnet=SUBNET : --subnet-region=SUBNET_REGION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime resource - User-defined unique name of this runtime. The runtime
name must be 1 to 63 characters long and contain only lowercase letters,
numeric characters, and dashes. The first character must be a lowercase
letter and the last character cannot be a dash. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument runtime on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME
     ID of the runtime or fully qualified identifier for the runtime.

     To set the runtime attribute:
     + provide the argument runtime on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this runtime
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument runtime on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--post-startup-script-option` | one of: POST_STARTUP_SCRIPT_OPTION_UNSPECIFIED, POST_STARTUP_SCRIPT_OPTION_SKIP, POST_STARTUP_SCRIPT_OPTION_RERUN | POST_STARTUP_SCRIPT_OPTION_UNSPECIFIED | Specifies the behavior of post startup script during migration. POST_STARTUP_SCRIPT_OPTION must be one of: POST_STARTUP_SCRIPT_OPTION_UNSPECIFIED, POST_STARTUP_SCRIPT_OPTION_SKIP, POST_STARTUP_SCRIPT_OPTION_RERUN. |
| `--service-account` | SERVICE_ACCOUNT |  | The service account to be included in the Compute Engine instance of the new Workbench Instance when the Runtime uses single user only mode for permission. If not specified, the Compute Engine default service account (https://cloud.google.com/compute/docs/access/service-accounts#default_service_account) is used. When the Runtime uses service account mode for permission, it will reuse the same service account, and this field must be empty. |


**Examples:**
```bash
To migrate a runtime, run:

    $ gcloud notebooks runtimes migrate example-runtime \
      --location=us-central1

To migrate a runtime with a new custom network, run:

    $ gcloud notebooks runtimes migrate example-runtime \
      --location=us-central1 \
      --network=projects/example-project/global/networks/\
    example-network \
        --subnet=projects/example-project/regions/us-central1/\
    subnetworks/example-subnetwork

To migrate a runtime and reuse the post-startup script, run:

    $ gcloud notebooks runtimes migrate example-runtime \
      --location=us-central1 \
      --post-startup-script-option=POST_STARTUP_SCRIPT_OPTION_RERUN
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/runtimes/migrate)

---
### `gcloud notebooks runtimes reset`

Request for resetting runtimes

Request for resetting notebook runtimes.

**Synopsis:**
```
gcloud notebooks runtimes reset (RUNTIME : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime resource - User-defined unique name of this runtime. The runtime
name must be 1 to 63 characters long and contain only lowercase letters,
numeric characters, and dashes. The first character must be a lowercase
letter and the last character cannot be a dash. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument runtime on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME
     ID of the runtime or fully qualified identifier for the runtime.

     To set the runtime attribute:
     + provide the argument runtime on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this runtime
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument runtime on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To reset a runtime, run:

    $ gcloud notebooks runtimes reset example-runtime \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/runtimes/reset)

---
### `gcloud notebooks runtimes start`

Request for starting runtimes

Request for starting notebook runtimes.

**Synopsis:**
```
gcloud notebooks runtimes start (RUNTIME : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime resource - User-defined unique name of this runtime. The runtime
name must be 1 to 63 characters long and contain only lowercase letters,
numeric characters, and dashes. The first character must be a lowercase
letter and the last character cannot be a dash. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument runtime on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME
     ID of the runtime or fully qualified identifier for the runtime.

     To set the runtime attribute:
     + provide the argument runtime on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this runtime
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument runtime on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To start a runtime, run:

    $ gcloud notebooks runtimes start example-runtime \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/runtimes/start)

---
### `gcloud notebooks runtimes stop`

Request for stopping runtimes

Request for stopping notebook runtimes.

**Synopsis:**
```
gcloud notebooks runtimes stop (RUNTIME : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime resource - User-defined unique name of this runtime. The runtime
name must be 1 to 63 characters long and contain only lowercase letters,
numeric characters, and dashes. The first character must be a lowercase
letter and the last character cannot be a dash. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument runtime on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME
     ID of the runtime or fully qualified identifier for the runtime.

     To set the runtime attribute:
     + provide the argument runtime on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this runtime
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument runtime on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To stop a runtime, run:

    $ gcloud notebooks runtimes stop example-runtime \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/runtimes/stop)

---
### `gcloud notebooks runtimes switch`

Request for switching runtimes

Request for switching notebook runtimes.

**Synopsis:**
```
gcloud notebooks runtimes switch (RUNTIME : --location=LOCATION) [--async]
    [--machine-type=MACHINE_TYPE]
    [--accelerator-core-count=ACCELERATOR_CORE_COUNT
      --accelerator-type=ACCELERATOR_TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime resource - User-defined unique name of this runtime. The runtime
name must be 1 to 63 characters long and contain only lowercase letters,
numeric characters, and dashes. The first character must be a lowercase
letter and the last character cannot be a dash. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument runtime on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME
     ID of the runtime or fully qualified identifier for the runtime.

     To set the runtime attribute:
     + provide the argument runtime on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this runtime
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument runtime on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--machine-type` | MACHINE_TYPE |  | machine type |
| `--accelerator-core-count` | ACCELERATOR_CORE_COUNT |  | Count of cores of this accelerator. |
| `--accelerator-type` | one of: NVIDIA_TESLA_A100, NVIDIA_TESLA_K80, NVIDIA_TESLA_P100, NVIDIA_TESLA_V100, NVIDIA_TESLA_P4, NVIDIA_TESLA_T4, NVIDIA_TESLA_T4_VWS, NVIDIA_TESLA_P100_VWS, NVIDIA_TESLA_P4_VWS, TPU_V2, TPU_V3 |  | Type of this accelerator. ACCELERATOR_TYPE must be one of: NVIDIA_TESLA_A100, NVIDIA_TESLA_K80, NVIDIA_TESLA_P100, NVIDIA_TESLA_V100, NVIDIA_TESLA_P4, NVIDIA_TESLA_T4, NVIDIA_TESLA_T4_VWS, NVIDIA_TESLA_P100_VWS, NVIDIA_TESLA_P4_VWS, TPU_V2, TPU_V3. |


**Examples:**
```bash
To switch a runtime, run:

    $ gcloud notebooks runtimes switch example-runtime \
      --machine-type=n1-standard-4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/runtimes/switch)

---