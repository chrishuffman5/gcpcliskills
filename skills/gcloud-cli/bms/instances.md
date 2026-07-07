# gcloud bms instances

manage bare metal instances in Bare Metal Solution

### `gcloud bms instances describe`

Describe a Bare Metal solution instance

Describe a Bare Metal Solution instance.

**Synopsis:**
```
gcloud bms instances describe (INSTANCE : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - instance. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To get a description of an instance called my-instance in project
my-project and region us-central1, run:

    $ gcloud bms instances describe my-instance --project=my-project \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/instances/describe)

---
### `gcloud bms instances disable-serial-console`

Disable interactive serial console for a Bare Metal Solution instance

Disables interactive serial console for a Bare Metal Solution instance.

**Synopsis:**
```
gcloud bms instances disable-serial-console (INSTANCE : --region=REGION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Bare Metal
Solution instance you want to disable interactive serial console for. The
arguments in this group can be used to specify the attributes of this
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

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To disable interactive serial console for an instance named test-instance,
run:

    $ gcloud bms instances disable-serial-console test-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/instances/disable-serial-console)

---
### `gcloud bms instances enable-serial-console`

Enable interactive serial console for a Bare Metal Solution instance

Enables interactive serial console for a Bare Metal Solution instance.

**Synopsis:**
```
gcloud bms instances enable-serial-console (INSTANCE : --region=REGION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Bare Metal
Solution instance you want to enable interactive serial console for. The
arguments in this group can be used to specify the attributes of this
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

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To enable interactive serial console for an instance named test-instance,
run:

    $ gcloud bms instances enable-serial-console test-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/instances/enable-serial-console)

---
### `gcloud bms instances list`

List Bare Metal Solution instances in a project

List Bare Metal Solution instances in a project.

**Synopsis:**
```
gcloud bms instances list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list instances in the region within the project us-central1, run:

    $ gcloud bms instances list --region=us-central1

Or:

To list all instances in the project, run:

    $ gcloud bms instances list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/instances/list)

---
### `gcloud bms instances rename`

Rename a Bare Metal Solution instance

Rename a Bare Metal Solution instance.

**Synopsis:**
```
gcloud bms instances rename (INSTANCE : --region=REGION)
    --new-name=NEW_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - instance. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--new-name` | NEW_NAME |  | New instance name for renaming an already existing instance. |


**Examples:**
```bash
To rename an instance my-instance to my-new-instance-name in region
us-central1, run:

    $ gcloud bms instances rename my-instance \
        --new-name=my-new-instance-name --region=us-central1 \
        --project=bms-example-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/instances/rename)

---
### `gcloud bms instances reset`

Reset a Bare Metal Solution instance

Perform a hard reset on a Bare Metal Solution instance.

This will not perform a clean shutdown of the OS on the instance.

**Synopsis:**
```
gcloud bms instances reset (INSTANCE : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Bare Metal
Solution instance you want to reset. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To reset an instance named test-instance, run:

    $ gcloud bms instances reset test-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/instances/reset)

---
### `gcloud bms instances start`

Start a Bare Metal Solution instance

Starts up a Bare Metal Solution instance.

**Synopsis:**
```
gcloud bms instances start (INSTANCE : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Bare Metal
Solution instance you want to start. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To start an instance named test-instance, run:

    $ gcloud bms instances start test-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/instances/start)

---
### `gcloud bms instances stop`

Stop a Bare Metal Solution instance

Stops a Bare Metal Solution instance.

**Synopsis:**
```
gcloud bms instances stop (INSTANCE : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Bare Metal
Solution instance you want to stop. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To stop an instance named test-instance, run:

    $ gcloud bms instances stop test-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/instances/stop)

---
### `gcloud bms instances update`

Update a Bare Metal Solution instance

Update a Bare Metal Solution instance.

This call returns immediately, but the update operation may take several
minutes to complete. To check if the operation is complete, use the
describe command for the instance.

**Synopsis:**
```
gcloud bms instances update (INSTANCE : --region=REGION) [--async]
    [--[no-]enable-hyperthreading] [--os-image=OS_IMAGE]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - instance. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--[no-]enable-hyperthreading` |  |  | Enable hyperthreading for the server. Use --enable-hyperthreading to enable and --no-enable-hyperthreading to disable. |
| `--os-image` | OS_IMAGE |  | OS image to install on the server. To list all OS image codes supported by BMS, run: $ gcloud bms os-images list |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update an instance called my-instance in region us-central1 with a new
label key1=value1, run:

    $ gcloud bms instances update my-instance --region=us-central1 \
        --update-labels=key1=value1

To clear all labels, run:

    $ gcloud bms instances update my-instance --region=us-central1 \
        --clear-labels
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/instances/update)

---