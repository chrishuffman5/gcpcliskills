# gcloud immersive-stream xr

manage Immersive Stream resources


## `gcloud immersive-stream xr contents` — manage Immersive Stream for XR contents
### `gcloud immersive-stream xr contents build`

Build an Immersive Stream for XR content resource

Build an Immersive Stream for XR content resource and tag it with a user
specified version tag.

**Synopsis:**
```
gcloud immersive-stream xr contents build (CONTENT : --location=LOCATION)
    --version=VERSION [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Content resource - Immersive Stream for XR content resource to be built.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument content on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONTENT
     ID of the content or fully qualified identifier for the content.

     To set the content attribute:
     + provide the argument content on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Global location name.

     To set the location attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | User-specified version tag of content build. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To build a content resource my-content tagged with version tag my-version,
run:

    $ gcloud immersive-stream xr contents build my-content \
        --version=my-version
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/immersive-stream/xr/contents/build)

---
### `gcloud immersive-stream xr contents create`

Create an Immersive Stream for XR content resource

Create an Immersive Stream for XR content resource.

**Synopsis:**
```
gcloud immersive-stream xr contents create (CONTENT : --location=LOCATION)
    --bucket=BUCKET [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Content resource - Immersive Stream for XR content resource to be created.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument content on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONTENT
     ID of the content or fully qualified identifier for the content.

     To set the content attribute:
     + provide the argument content on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Global location name.

     To set the location attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | The name of the Cloud Storage bucket in the consumer project that stores the content source. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To create a content resource called my-content using Cloud Storage bucket
my-bucket, run:

    $ gcloud immersive-stream xr contents create my-content \
        --bucket=my-bucket
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/immersive-stream/xr/contents/create)

---
### `gcloud immersive-stream xr contents delete`

Delete an Immersive Stream for XR content resource

Delete an Immersive Stream for XR content resource.

**Synopsis:**
```
gcloud immersive-stream xr contents delete (CONTENT : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Content resource - Immersive Stream for XR content resource to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument content on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONTENT
     ID of the content or fully qualified identifier for the content.

     To set the content attribute:
     + provide the argument content on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Global location name.

     To set the location attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a content called my-content, run:

    $ gcloud immersive-stream xr contents delete my-content
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/immersive-stream/xr/contents/delete)

---
### `gcloud immersive-stream xr contents describe`

Describe a specific Immersive Stream for XR content resource

Describe a specific Immersive Stream for XR content resource.

**Synopsis:**
```
gcloud immersive-stream xr contents describe
    (CONTENT : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Content resource - The name of the content resource you want to describe.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument content on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONTENT
     ID of the content or fully qualified identifier for the content.

     To set the content attribute:
     + provide the argument content on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Global location name.

     To set the location attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Examples:**
```bash
To describe the content, run:

    $ gcloud immersive-stream xr contents describe my-content
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/immersive-stream/xr/contents/describe)

---
### `gcloud immersive-stream xr contents list`

List Immersive Stream for XR content resources

List Immersive Stream for XR content resources.

**Synopsis:**
```
gcloud immersive-stream xr contents list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + global is the only supported location. |


**Examples:**
```bash
To list Immersive Stream for XR content resources, run:

    $ gcloud immersive-stream xr contents list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/immersive-stream/xr/contents/list)

---
### `gcloud immersive-stream xr contents update`

Update an Immersive Stream for XR content resource

Update an Immersive Stream for XR content resource.

**Synopsis:**
```
gcloud immersive-stream xr contents update (CONTENT : --location=LOCATION)
    --bucket=BUCKET [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Content resource - Immersive Stream for XR content resource to be updated.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument content on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONTENT
     ID of the content or fully qualified identifier for the content.

     To set the content attribute:
     + provide the argument content on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Global location name.

     To set the location attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | The name of the Cloud Storage bucket in the consumer project that stores the content source. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To update the Cloud Storage bucket used by the content resource my-content,
to my-new-bucket run:

    $ gcloud immersive-stream xr contents update my-content \
        --bucket=my-new-bucket
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/immersive-stream/xr/contents/update)

---

## `gcloud immersive-stream xr instances` — manage Immersive Stream for XR instances
### `gcloud immersive-stream xr instances create`

Create an Immersive Stream for XR service instance

Create an Immersive Stream for XR service instance.

**Synopsis:**
```
gcloud immersive-stream xr instances create INSTANCE
    --add-region=[autoscaling_buffer=AUTOSCALING_BUFFER],
      [autoscaling_min_capacity=AUTOSCALING_MIN_CAPACITY],
      [capacity=CAPACITY],
      [enable_autoscaling=ENABLE_AUTOSCALING],[region=REGION]
    --version=VERSION (--content=CONTENT : --location=LOCATION) [--async]
    [--fallback-url=FALLBACK_URL] [--gpu-class=GPU_CLASS] [--mode=MODE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Name of the instance to be created
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--add-region` | [autoscaling_buffer=AUTOSCALING_BUFFER],[autoscaling_min_capacity=AUTOSCALING_MIN_CAPACITY],[capacity=CAPACITY],[enable_autoscaling=ENABLE_AUTOSCALING],[region=REGION] |  | Flag used to specify region and capacity required for the service instance's availability. 'region' is the region in which the instance is deployed. 'capacity' is the maxium number of concurrent streaming sessions that the instance can support in the given region. This is a repeatable flag. |
| `--version` | VERSION |  | Build version tag of the content served by this instance |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--fallback-url` | FALLBACK_URL |  | Fallback url to redirect users to when this service instance is unable to provide the streaming experience |
| `--gpu-class` | GPU_CLASS |  | The class of GPU that is used by this service instance |
| `--mode` | MODE |  | The rendering mode that is supported by this service instance |


**Examples:**
```bash
To create a service instance called my-instance serving content my-content
with version my-version that has availablilty for 2 concurent sessions in
us-west1 region and 3 concurrent sessions in us-east4 region, run:

    $ gcloud immersive-stream xr instances create my-instance \
        --content=my-content --version=my-version \
        --add-region=region=us-west1,capacity=2 \
        --add-region=region=us-east4,capacity=3

Optionally, a fallback url may be specified. Users will be redirected to
this fallback url when the service instance is unable to provide the
streaming experience. To create a service instance called my-instance
serving content my-content with version my-version that has availablilty
for 2 concurent sessions in us-west1 and uses fallback url
https://www.google.com run:

    $ gcloud immersive-stream xr instances create my-instance \
        --content=my-content --version=my-version \
        --add-region=region=us-west1,capacity=2 \
        --fallback-url="https://www.google.com"

    By default, the instance is created with mode=ar, which supports both
    3D and AR experiences. Instances can also be configured to use
    3D-only mode. This configuration cannot be updated later.
    To use 3D-only mode, include:

    --mode=3d

    By default, the instance is created with gpu-class=t4. This uses the
    NVIDIA T4 GPU for the instance. Instances can also be configured to
    use NVIDIA L4 GPUs at creation. Note that only certain regions are
    available for L4, and only 3D-only mode is supported. This
    configuration cannot be updated later.
    To use NVIDIA L4 GPU for the instance, include:

    --gpu-class=l4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/immersive-stream/xr/instances/create)

---
### `gcloud immersive-stream xr instances delete`

Delete an Immersive Stream for XR service instance

Delete an Immersive Stream for XR service instance.

**Synopsis:**
```
gcloud immersive-stream xr instances delete
    (INSTANCE : --location=LOCATION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Immersive Stream for XR service instance to delete.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Global location name.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a service instance called my-instance, run:

    $ gcloud immersive-stream xr instances delete my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/immersive-stream/xr/instances/delete)

---
### `gcloud immersive-stream xr instances describe`

Describe a specific Immersive Stream for XR service instance

Describe a specific Immersive Stream for XR service instance.

**Synopsis:**
```
gcloud immersive-stream xr instances describe
    (INSTANCE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The name of the service instance you want to describe.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Global location name.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Examples:**
```bash
To describe the service instance, run:

    $ gcloud immersive-stream xr instances describe my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/immersive-stream/xr/instances/describe)

---
### `gcloud immersive-stream xr instances list`

List Immersive Stream for XR service instances

List Immersive Stream for XR service instances.

**Synopsis:**
```
gcloud immersive-stream xr instances list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + global is the only supported location. |


**Examples:**
```bash
To list Immersive Stream for XR service instances, run:

    $ gcloud immersive-stream xr instances list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/immersive-stream/xr/instances/list)

---
### `gcloud immersive-stream xr instances update`

Update an Immersive Stream for XR service instance

Update an Immersive Stream for XR service instance. This command can be
used to update one of the following:
  o the capacity for an existing region of the service instance
  o the content build version served by the instance
  o the fallback url to redirect users to when the service instance is
    unable to provide the streaming experience

If updating the capacity, only one region may be updated for each command
execution, and the new capacity may not be 0 or exceed the quota limit.

**Synopsis:**
```
gcloud immersive-stream xr instances update
    (INSTANCE : --location=LOCATION)
    (--add-region=[autoscaling_buffer=AUTOSCALING_BUFFER],
      [autoscaling_min_capacity=AUTOSCALING_MIN_CAPACITY],
      [capacity=CAPACITY],
      [enable_autoscaling=ENABLE_AUTOSCALING],[region=REGION]
      | --fallback-url=FALLBACK_URL | --remove-region=REMOVE_REGION
      | --update-region=[autoscaling_buffer=AUTOSCALING_BUFFER],
      [autoscaling_min_capacity=AUTOSCALING_MIN_CAPACITY],
      [capacity=CAPACITY],
      [enable_autoscaling=ENABLE_AUTOSCALING],[region=REGION]
      | --version=VERSION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Immersive Stream for XR service instance to update.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the name attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the instance.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + location is always global.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--add-region` | [autoscaling_buffer=AUTOSCALING_BUFFER],[autoscaling_min_capacity=AUTOSCALING_MIN_CAPACITY],[capacity=CAPACITY],[enable_autoscaling=ENABLE_AUTOSCALING],[region=REGION] |  | _[Exactly one of these must be specified:]_ Flag used to specify region and capacity required for the service instance's availability. 'region' is the region in which the instance is deployed. 'capacity' is the maxium number of concurrent streaming sessions that the instance can support in the given region. |
| `--fallback-url` | FALLBACK_URL |  | _[Exactly one of these must be specified:]_ Fallback url to redirect users to when this service instance is unable to provide the streaming experience |
| `--remove-region` | REMOVE_REGION |  | _[Exactly one of these must be specified:]_ Region to remove |
| `--update-region` | [autoscaling_buffer=AUTOSCALING_BUFFER],[autoscaling_min_capacity=AUTOSCALING_MIN_CAPACITY],[capacity=CAPACITY],[enable_autoscaling=ENABLE_AUTOSCALING],[region=REGION] |  | _[Exactly one of these must be specified:]_ Flag used to specify region and capacity required for the service instance's availability. 'region' is the region in which the instance is deployed. 'capacity' is the maxium number of concurrent streaming sessions that the instance can support in the given region. |
| `--version` | VERSION |  | _[Exactly one of these must be specified:]_ Build version tag of the content served by this instance |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To update the service instance my-instance to have capacity 2 for an
existing region us-west1, run:

    $ gcloud immersive-stream xr instances update my-instance \
        --update-region=region=us-west1,capacity=2

To update the service instance my-instance to have capacity 1 for a new
region us-east4, run:

    $ gcloud immersive-stream xr instances update my-instance \
        --add-region=region=us-east4,capacity=1

To update the service instance my-instance to remove the existing region
us-east4, run:

    $ gcloud immersive-stream xr instances update my-instance \
        --remove-region=us-east4

To update the service instance my-instance to serve content version
my-version, run:

    $ gcloud immersive-stream xr instances update my-instance \
        --version=my-version

To update the service instance my-instance to use fallback url
https://www.google.com, run:

    $ gcloud immersive-stream xr instances update my-instance \
        --fallback-url="https://www.google.com"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/immersive-stream/xr/instances/update)

---

## `gcloud immersive-stream xr operations` — manage Immersive Stream for XR operations
### `gcloud immersive-stream xr operations describe`

Get description of a long-running Immersive Stream for XR operation

Get information about a long-running Immersive Stream for XR operation.

**Synopsis:**
```
gcloud immersive-stream xr operations describe
    (OPERATION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The ID of the operation to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Global location name.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Examples:**
```bash
To get information about a long-running operation with name
projects/my-project/locations/global/operations/operation-123, run the
following command:

    $ gcloud immersive-stream xr operations describe \
        projects/my-project/locations/global/operations/operation-123

or simply run

    $ gcloud immersive-stream xr operations describe operation-123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/immersive-stream/xr/operations/describe)

---
### `gcloud immersive-stream xr operations list`

List Immersive Stream for XR operations

List Immersive Stream for XR operations.

**Synopsis:**
```
gcloud immersive-stream xr operations list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + global is the only supported location. |


**Examples:**
```bash
To list Immersive Stream for XR operations, run:

    $ gcloud immersive-stream xr operations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/immersive-stream/xr/operations/list)

---
### `gcloud immersive-stream xr operations wait`

Poll long-running Immersive Stream for XR operation until it completes

Poll a long-running Immersive Stream for XR operation until it completes.
When the operation is complete, this command will display the results of
the analysis.

**Synopsis:**
```
gcloud immersive-stream xr operations wait
    (OPERATION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The ID of the operation to poll until complete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Global location name.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Examples:**
```bash
To poll a long-running Immersive Stream for XR operation named
projects/my-project/locations/global/operations/operation-123 until it
completes, run the following:

    $ gcloud immersive-stream xr operations wait \
        projects/my-project/locations/global/operations/operation-123

or simply run

    $ gcloud immersive-stream xr operations wait operation-123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/immersive-stream/xr/operations/wait)

---