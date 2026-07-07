# gcloud compute tpus

list, create, and delete Cloud TPUs


## `gcloud compute tpus accelerator-types` — list or Describe Available Cloud TPU accelerator types
### `gcloud compute tpus accelerator-types describe`

Describe an accelerator type available for Cloud TPUs

Get details on an accelerator type.

To get a list of available accelerator types for your location run:

    $ gcloud compute tpus accelerator-types list

**Synopsis:**
```
gcloud compute tpus accelerator-types describe
    (ACCELERATOR_TYPE : --zone=ZONE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Accelerator type resource - The accelerator type you want to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument accelerator_type on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ACCELERATOR_TYPE
     ID of the accelerator_type or fully qualified identifier for the
     accelerator_type.

     To set the accelerator_type attribute:
     + provide the argument accelerator_type on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The compute/zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument accelerator_type on the command line with a
       fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
The following command describes the v3-8 accelerator types running in zone
us-central1-b:

    $ gcloud compute tpus accelerator-types describe v3-8 \
        --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/accelerator-types/describe)

---
### `gcloud compute tpus accelerator-types list`

List available accelerator types for Cloud TPUs

List available accelerator types for for Cloud TPUs.

**Synopsis:**
```
gcloud compute tpus accelerator-types list [--zone=ZONE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the zone attribute: + provide the argument --zone on the command line; + set the property compute/zone. |


**Examples:**
```bash
The following command lists all of the accelerator types available in zone
us-central1-b:

    $ gcloud compute tpus accelerator-types list --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/accelerator-types/list)

---

## `gcloud compute tpus locations` — list or Describe Available Cloud TPU Locations
### `gcloud compute tpus locations describe`

Describe a Cloud TPU Location

Describe a Cloud TPU Location.

To get a list of available locations for your project run:

    $ gcloud compute tpus locations list

**Synopsis:**
```
gcloud compute tpus locations describe [ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Location resource - The Cloud TPU Location you want to describe. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * set the property compute/zone with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [ZONE]
     ID of the location or fully qualified identifier for the location.

     To set the zone attribute:
     + provide the argument zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
The following command describes the TPUs running in zone us-central1-b:

    $ gcloud compute tpus locations describe us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/locations/describe)

---
### `gcloud compute tpus locations list`

List available locations for Cloud TPUs

List available locations for Cloud TPUs.

**Synopsis:**
```
gcloud compute tpus locations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists all of the zones where TPUs are available:

    $ gcloud compute tpus locations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/locations/list)

---

## `gcloud compute tpus queued-resources` — list, create, delete, and manage Queued Resources
### `gcloud compute tpus queued-resources create`

Create a Queued Resource

Create a new Queued Resource with the specified attributes.

**Synopsis:**
```
gcloud compute tpus queued-resources create (QUEUED_RESOURCE : --zone=ZONE)
    --runtime-version=RUNTIME_VERSION
    (--accelerator-type=ACCELERATOR_TYPE | --topology=TOPOLOGY --type=TYPE)
    (--node-id=NODE_ID
      | [--node-count=NODE_COUNT : --node-prefix=NODE_PREFIX]) [--async]
    [--boot-disk=[KEY=VALUE,...]] [--data-disk=[mode=MODE],[source=SOURCE]]
    [--description=DESCRIPTION] [--guaranteed] [--internal-ips]
    [--labels=[KEY=VALUE,...]] [--metadata=[KEY=VALUE,...]]
    [--metadata-from-file=[KEY=VALUE,...]]
    [--network=NETWORK; default="default"] [--range=RANGE] [--reserved]
    [--scopes=[SCOPES,...]] [--service-account=SERVICE_ACCOUNT]
    [--shielded-secure-boot] [--spot] [--subnetwork=SUBNETWORK]
    [--tags=[TAGS,...]] [--valid-after-duration=VALID_AFTER_DURATION]
    [--valid-after-time=VALID_AFTER_TIME]
    [--valid-until-duration=VALID_UNTIL_DURATION]
    [--valid-until-time=VALID_UNTIL_TIME]
    [--reservation-host-folder=RESERVATION_HOST_FOLDER
      --reservation-host-organization=RESERVATION_HOST_ORGANIZATION
      --reservation-host-project=RESERVATION_HOST_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Queued resource resource - The Queued Resource you want to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument queued_resource on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  QUEUED_RESOURCE
     ID of the queued_resource or fully qualified identifier for the
     queued_resource.

     To set the queued_resource attribute:
     + provide the argument queued_resource on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The compute/zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument queued_resource on the command line with a
       fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--runtime-version` | RUNTIME_VERSION |  | Runtime version for the TPU, such as tpu-ubuntu2204-base. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--boot-disk` | [KEY=VALUE,...] |  | Specifies the boot disk configuration. $ gcloud compute tpus queued-resources create \ --boot-disk kms-key=<full_kms_key_name_here> The following keys are allowed: kms-key Specifies the fully qualified Cloud KMS cryptokey name which will be used to protect the disk. KMS cryptokey name format: projects/<kms-project>/locations/<kms-location>/keyRings/<kms-keyring>/cryptoKeys/<key-name> |
| `--data-disk` | [mode=MODE],[source=SOURCE] |  | Additional data disks for the TPU VM. This flag must be repeated to provide multiple data disks. For example: $ gcloud compute tpus queued-resources create \ --data-disk \ source=projects/my-project/zones/us-central1-c/disks/my-disk,\ mode=read-only The following keys are allowed: source Specifies the full path to an existing disk. Required. The disk must be in the same zone. mode Specifies the mode in which to attach this disk. Valid options are 'read-write', 'read-only'. If not specified, the default is 'read-write'. |
| `--description` | DESCRIPTION |  | Text description of the TPU. |
| `--guaranteed` |  |  | If provided, the Node requested here will only be scheduled at the 'guaranteed' tier. |
| `--internal-ips` |  |  | Indicates that the IP addresses for the node should be internal. The default is that external IP addresses will be associated with the TPU workers. |
| `--labels` | [KEY=VALUE,...] |  | Resource labels to represent user-provided metadata. See https://cloud.google.com/compute/docs/labeling-resources for details. |
| `--metadata` | [KEY=VALUE,...] |  | List of comma-separated metadata key-value pairs for the Cloud TPU VM node. Example: --metadata='key1=value1,key2=value2' |
| `--metadata-from-file` | [KEY=VALUE,...] |  | Same as --metadata except the value for the entry will be read from a local file. Example: --metadata-from-file='key1=value1.txt' |
| `--network` | NETWORK | default | Network that this TPU will be a part of. |
| `--range` | RANGE |  | CIDR range for the TPU. The IP range that the TPU will select an IP address from. Must be in CIDR notation and a /29 range, for example 192.168.0.0/29. Errors will occur if the CIDR range has already been used for a currently existing TPU, the CIDR range conflicts with any networks in the user's provided network, or the provided network is peered with another network that is using that CIDR range. |
| `--reserved` |  |  | Specifies the request should be scheduled on reserved capacity. If --reservation-host-project, --reservation-host-folder, or --reservation-host-organization are present then this flag has no effect. |
| `--scopes` | [SCOPES,...] |  | List of comma-separated scopes to be made available for the service account. |
| `--service-account` | SERVICE_ACCOUNT |  | Email address of the service account. If empty, default Google Compute Engine service account will be used. |
| `--shielded-secure-boot` |  |  | Specifies that the TPU instances are created with secure boot enabled. This implicitly makes them Shielded VM instances. |
| `--spot` |  |  | If provided, the Node requested here will be created as Spot VMs. |
| `--subnetwork` | SUBNETWORK |  | Subnetwork that this TPU will be a part of. |
| `--tags` | [TAGS,...] |  | Tags to apply to the TPU Node. Tags are used to identify valid sources or targets for network firewalls. See https://cloud.google.com/vpc/docs/add-remove-network-tags for more details. |
| `--valid-after-duration` | VALID_AFTER_DURATION |  | A duration before which the TPU must not be provisioned, relative to the current time. See $ gcloud topic datetimes for information on duration formats. |
| `--valid-after-time` | VALID_AFTER_TIME |  | An absolute time before which the TPU must not be provisioned. See $ gcloud topic datetimes for information on duration formats. |
| `--valid-until-duration` | VALID_UNTIL_DURATION |  | A duration after which the TPU must not be provisioned, relative to the current time. See $ gcloud topic datetimes for information on duration formats. |
| `--valid-until-time` | VALID_UNTIL_TIME |  | An absolute time after which resources must not be created. See $ gcloud topic datetimes for information on duration formats. |
| `--reservation-host-folder` | RESERVATION_HOST_FOLDER |  | The folder hosting the reservation that the TPU should use. Only one reservation host entity may be specified. |
| `--reservation-host-organization` | RESERVATION_HOST_ORGANIZATION |  | The organization hosting the reservation that the TPU should use. Only one reservation host entity may be specified. |
| `--reservation-host-project` | RESERVATION_HOST_PROJECT |  | The project hosting the reservation that the TPU should use. Only one reservation host entity may be specified. |


**Examples:**
```bash
To create a Queued Resource with ID my-queued-resource in zone
us-central2-b and project my-project, run:

    $ gcloud compute tpus queued-resources create my-queued-resource \
        --accelerator-type=v4-8 --runtime-version=v2-alpha-tpuv4 \
        --node-id=my-node-001 --zone=us-central2-b --project=my-project

To create a Queued Resource with multiple nodes, run:

    $ gcloud compute tpus queued-resources create my-queued-resource \
        --accelerator-type=v4-8 --runtime-version=v2-alpha-tpuv4 \
        --node-count=2 --zone=us-central2-b --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/queued-resources/create)

---
### `gcloud compute tpus queued-resources delete`

Delete a Queued Resource

Delete an existing Queued Resource.

To get a list of Queued Resources for deletion, run:

    $ gcloud compute tpus queued-resources list

**Synopsis:**
```
gcloud compute tpus queued-resources delete (QUEUED_RESOURCE : --zone=ZONE)
    [--async] [--force] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Queued resource resource - The Queued Resource you want to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument queued_resource on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  QUEUED_RESOURCE
     ID of the queued_resource or fully qualified identifier for the
     queued_resource.

     To set the queued_resource attribute:
     + provide the argument queued_resource on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The compute/zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument queued_resource on the command line with a
       fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | If set to true, any nodes in this queued resource will also be deleted. Otherwise, the request will only work if the queued resource has no nodes. |


**Examples:**
```bash
To delete a Queued Resource with ID my-queued-resource in zone
us-central1-b and project my-project, run:

    $ gcloud compute tpus queued-resources delete my-queued-resource \
        --zone=us-central1-b --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/queued-resources/delete)

---
### `gcloud compute tpus queued-resources describe`

Describe a Queued Resource

Get details on a Queued Resource.

To get a list of Queued Resources to describe in more detail, run:

    $ gcloud compute tpus queued-resources list

**Synopsis:**
```
gcloud compute tpus queued-resources describe
    (QUEUED_RESOURCE : --zone=ZONE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Queued resource resource - The Queued Resource you want to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument queued_resource on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  QUEUED_RESOURCE
     ID of the queued_resource or fully qualified identifier for the
     queued_resource.

     To set the queued_resource attribute:
     + provide the argument queued_resource on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The compute/zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument queued_resource on the command line with a
       fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To describe a Queued Resource with ID my-queued-resource in zone
us-central1-b and project 'my-project', run:

    $ gcloud compute tpus queued-resources describe my-queued-resource \
        --zone=us-central1-b --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/queued-resources/describe)

---
### `gcloud compute tpus queued-resources list`

List Queued Resources

List all Queued Resources associated with a project and location.

**Synopsis:**
```
gcloud compute tpus queued-resources list [--zone=ZONE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the zone attribute: + provide the argument --zone on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list all Queued Resources available in zone us-central1-b for project
my-project, run:

    $ gcloud compute tpus queued-resources list --zone=us-central1-b \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/queued-resources/list)

---
### `gcloud compute tpus queued-resources reset`

Reset a Queued Resource

Reset an existing Queued Resource.

To get a list of Queued Resources for resetting, run:

    $ gcloud compute tpus queued-resources list

**Synopsis:**
```
gcloud compute tpus queued-resources reset (QUEUED_RESOURCE : --zone=ZONE)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Queued resource resource - The Queued Resource you want to reset. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument queued_resource on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  QUEUED_RESOURCE
     ID of the queued_resource or fully qualified identifier for the
     queued_resource.

     To set the queued_resource attribute:
     + provide the argument queued_resource on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The compute/zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument queued_resource on the command line with a
       fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To reset a Queued Resource in zone us-central1-b and project my-project,
run:

    $ gcloud compute tpus queued-resources reset --zone=us-central1-b \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/queued-resources/reset)

---
### `gcloud compute tpus queued-resources scp`

Copy files to and from a Cloud TPU Queued Resource via SCP

Copy files to and from a Cloud TPU Queued Resource via SCP.

**Synopsis:**
```
gcloud compute tpus queued-resources scp [[USER@]INSTANCE:]SRC
    [[[USER@]INSTANCE:]SRC ...] [[USER@]INSTANCE:]DEST
    [--batch-size=BATCH_SIZE; default=64] [--compress] [--dry-run]
    [--force-key-file-overwrite] [--node=NODE; default="0"] [--plain]
    [--recurse] [--scp-flag=SCP_FLAG] [--ssh-key-file=SSH_KEY_FILE]
    [--strict-host-key-checking=STRICT_HOST_KEY_CHECKING]
    [--worker=WORKER; default="0"] [--zone=ZONE]
    [--internal-ip | --tunnel-through-iap]
    [--ssh-key-expiration=SSH_KEY_EXPIRATION
      | --ssh-key-expire-after=SSH_KEY_EXPIRE_AFTER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[[USER@]INSTANCE:]SRC [[[USER@]INSTANCE:]SRC ...]
   Specifies the files to copy.

[[USER@]INSTANCE:]DEST
   Specifies a destination for the source files.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--batch-size` | BATCH_SIZE | 64 | Batch size for simultaneous command execution on the client's side. When using a comma-separated list (e.g. '1,4,6') or a range (e.g. '1-3') or ``all`` keyword in --worker flag, it executes the command concurrently in groups of the batch size. This flag takes a value greater than 0 to specify the batch size to control the concurrent connections that can be established with the TPU workers, or the special keyword ``all`` to allow the concurrent command executions on all the specified workers in --worker flag. Maximum value of this flag should not be more than the number of specified workers, otherwise the value will be treated as ``--batch-size=all``. |
| `--compress` |  |  | Enable compression. |
| `--dry-run` |  |  | Print the equivalent scp/ssh command that would be run to stdout, instead of executing it. |
| `--force-key-file-overwrite` |  |  | If enabled, the gcloud command-line tool will regenerate and overwrite the files associated with a broken SSH key without asking for confirmation in both interactive and non-interactive environments. If disabled, the files associated with a broken SSH key will not be regenerated and will fail in both interactive and non-interactive environments. |
| `--node` | NODE | 0 | TPU node(s) to connect to. The supported value is a single 0-based index of the node(s) in the case of a TPU Pod. It additionally supports a comma-separated list (e.g. '1,4,6'), range (e.g. '1-3'), or special keyword ``all" to run the command concurrently on each of the specified node(s). Note that when targeting multiple nodes, you should run 'ssh-add' with your private key prior to executing the gcloud command. Default: 'ssh-add ~/.ssh/google_compute_engine'. |
| `--plain` |  |  | Suppress the automatic addition of ssh(1)/scp(1) flags. This flag is useful if you want to take care of authentication yourself or use specific ssh/scp features. |
| `--recurse` |  |  | Upload directories recursively. |
| `--scp-flag` | SCP_FLAG |  | Additional flags to be passed to scp(1). This flag may be repeated. |
| `--ssh-key-file` | SSH_KEY_FILE |  | The path to the SSH key file. By default, this is ~\.ssh\google_compute_engine. |
| `--strict-host-key-checking` | one of: yes, no, ask |  | Override the default behavior of StrictHostKeyChecking for the connection. By default, StrictHostKeyChecking is set to 'no' the first time you connect to an instance, and will be set to 'yes' for all subsequent connections. STRICT_HOST_KEY_CHECKING must be one of: yes, no, ask. |
| `--worker` | WORKER | 0 | TPU worker to connect to. The supported value is a single 0-based index of the worker in the case of a TPU Pod. When also using the --command flag, it additionally supports a comma-separated list (e.g. '1,4,6'), range (e.g. '1-3'), or special keyword ``all" to run the command concurrently on each of the specified workers. Note that when targeting multiple workers, you should run 'ssh-add' with your private key prior to executing the gcloud command. Default: 'ssh-add ~/.ssh/google_compute_engine'. |
| `--zone` | ZONE |  | Zone of the tpu to scp. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To copy a file (for example, a text file in the local home directory) to a
Cloud Queued Resource, run:

    $ gcloud compute tpus queued-resources scp ~/my-file my-qr:

To copy a file into all nodes and workers in a Cloud TPU Queued Resource
(with the default batch size), run:

    $ gcloud compute tpus queued-resources scp ~/my-file my-qr: \
      --worker=all --node=all

To copy a file into all nodes and workers in a Cloud TPU Queued Resource
with a batch size of 4, run:

    $ gcloud compute tpus queued-resources scp ~/my-file my-qr: \
      --worker=all --node=all --batch-size=4

To copy a file into all workers in the first node of a Cloud TPU Queued
Resource, run:

    $ gcloud compute tpus queued-resources scp ~/my-file my-qr: \
      --worker=all

To copy a file from a Cloud TPU Queued Resource to the home directory of
the local computer, run:

    $ gcloud compute tpus queued-resources scp my-qr:~/my-file ~/

To copy all files in a folder to a Cloud TPU Queued Resource, run:

    $ gcloud compute tpus queued-resources scp ~/my-folder/ my-qr: \
      --recurse
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/queued-resources/scp)

---
### `gcloud compute tpus queued-resources ssh`

SSH into a Cloud TPU Queued Resource's node(s)

Send SSH commands to a Cloud TPU Queued Resource.

**Synopsis:**
```
gcloud compute tpus queued-resources ssh [USER@]QR
    [--batch-size=BATCH_SIZE; default=64] [--dry-run]
    [--force-key-file-overwrite] [--node=NODE; default="0"] [--plain]
    [--ssh-flag=SSH_FLAG] [--ssh-key-file=SSH_KEY_FILE]
    [--strict-host-key-checking=STRICT_HOST_KEY_CHECKING]
    [--worker=WORKER; default="0"] [--zone=ZONE]
    [--command=COMMAND : --output-directory=OUTPUT_DIRECTORY]
    [--internal-ip | --tunnel-through-iap]
    [--ssh-key-expiration=SSH_KEY_EXPIRATION
      | --ssh-key-expire-after=SSH_KEY_EXPIRE_AFTER] [GCLOUD_WIDE_FLAG ...]
    [-- SSH_ARGS ...]
```

**Positional arguments:**
```
[USER@]QR
   Specifies the Cloud TPU Queued Resource to send SSH command to.

   USER specifies the username with which to SSH. If omitted, the user
   login name is used.

   QR specifies the name of the Cloud TPU Queued Resource to send SSH
   command to.

[-- SSH_ARGS ...]
   Flags and positionals passed to the underlying ssh implementation.

   The '--' argument must be specified between gcloud specific args on the
   left and SSH_ARGS on the right. Example:

       $ gcloud compute tpus queued-resources ssh example-instance \
       --zone=us-central1-a -- -vvv -L 80:%TPU%:80
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--batch-size` | BATCH_SIZE | 64 | Batch size for simultaneous command execution on the client's side. When using a comma-separated list (e.g. '1,4,6') or a range (e.g. '1-3') or ``all`` keyword in --worker flag, it executes the command concurrently in groups of the batch size. This flag takes a value greater than 0 to specify the batch size to control the concurrent connections that can be established with the TPU workers, or the special keyword ``all`` to allow the concurrent command executions on all the specified workers in --worker flag. Maximum value of this flag should not be more than the number of specified workers, otherwise the value will be treated as ``--batch-size=all``. |
| `--dry-run` |  |  | Print the equivalent scp/ssh command that would be run to stdout, instead of executing it. |
| `--force-key-file-overwrite` |  |  | If enabled, the gcloud command-line tool will regenerate and overwrite the files associated with a broken SSH key without asking for confirmation in both interactive and non-interactive environments. If disabled, the files associated with a broken SSH key will not be regenerated and will fail in both interactive and non-interactive environments. |
| `--node` | NODE | 0 | TPU node(s) to connect to. The supported value is a single 0-based index of the node(s) in the case of a TPU Pod. When also using the --command flag, it additionally supports a comma-separated list (e.g. '1,4,6'), range (e.g. '1-3'), or special keyword ``all" to run the command concurrently on each of the specified node(s). Note that when targeting multiple nodes, you should run 'ssh-add' with your private key prior to executing the gcloud command. Default: 'ssh-add ~/.ssh/google_compute_engine'. |
| `--plain` |  |  | Suppress the automatic addition of ssh(1)/scp(1) flags. This flag is useful if you want to take care of authentication yourself or use specific ssh/scp features. |
| `--ssh-flag` | SSH_FLAG |  | Additional flags to be passed to ssh(1). It is recommended that flags be passed using an assignment operator and quotes. Example: $ gcloud compute tpus queued-resources ssh example-instance \ --zone=us-central1-a --ssh-flag="-vvv" \ --ssh-flag="-L 80:localhost:80" This flag will replace occurences of %USER% and %TPU% with their dereferenced values. For example, passing ``80:%TPU%:80`` into the flag is equivalent to passing 80:162.222.181.197:80 to ssh(1) if the external IP address of 'example-instance' is 162.222.181.197. If connecting to the instance's external IP, then %TPU% is replaced with that, otherwise it is replaced with the internal IP. |
| `--ssh-key-file` | SSH_KEY_FILE |  | The path to the SSH key file. By default, this is ~\.ssh\google_compute_engine. |
| `--strict-host-key-checking` | one of: yes, no, ask |  | Override the default behavior of StrictHostKeyChecking for the connection. By default, StrictHostKeyChecking is set to 'no' the first time you connect to an instance, and will be set to 'yes' for all subsequent connections. STRICT_HOST_KEY_CHECKING must be one of: yes, no, ask. |
| `--worker` | WORKER | 0 | TPU worker to connect to. The supported value is a single 0-based index of the worker in the case of a TPU Pod. When also using the --command flag, it additionally supports a comma-separated list (e.g. '1,4,6'), range (e.g. '1-3'), or special keyword ``all" to run the command concurrently on each of the specified workers. Note that when targeting multiple workers, you should run 'ssh-add' with your private key prior to executing the gcloud command. Default: 'ssh-add ~/.ssh/google_compute_engine'. |
| `--zone` | ZONE |  | Zone of the tpu to ssh. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To run an SSH command in a Cloud TPU Queued Resource's first node and first
worker (for example, to print the time since last boot), run:

    $ gcloud compute tpus queued-resources ssh my-qr \
      --command="last boot"

To run the same command in all nodes and workers in a Cloud TPU Queued
Resource (with the default batch size), run:

    $ gcloud compute tpus queued-resources ssh my-qr \
      --command="last boot" --worker=all --node=all

To run the same command in all nodes and workers in a Cloud TPU Queued
Resource but batching the request in groups of 4, run:

    $ gcloud compute tpus queued-resources ssh my-qr \
      --command="last boot" --worker=all --node=all --batch-size=4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/queued-resources/ssh)

---

## `gcloud compute tpus topologies` — list available Cloud TPU topologies
### `gcloud compute tpus topologies list`

List available topologies for Cloud TPUs

List available topologies for for Cloud TPUs.

**Synopsis:**
```
gcloud compute tpus topologies list [--zone=ZONE] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the zone attribute: + provide the argument --zone on the command line; + set the property compute/zone. |


**Examples:**
```bash
The following command lists all of the topologies available in zone
us-central1-b:

    $ gcloud compute tpus topologies list --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/topologies/list)

---

## `gcloud compute tpus tpu-vm` — list, create, and manage Cloud TPU VM nodes
### `gcloud compute tpus tpu-vm create`

Create a new Cloud TPU VM node

Create a new Cloud TPU VM node.

**Synopsis:**
```
gcloud compute tpus tpu-vm create (TPU : --zone=ZONE) --version=VERSION
    [--async] [--boot-disk=[KEY=VALUE,...]]
    [--data-disk=[mode=MODE],[source=SOURCE]] [--description=DESCRIPTION]
    [--internal-ips] [--labels=[KEY=VALUE,...]]
    [--metadata=[KEY=VALUE,...]] [--metadata-from-file=[KEY=VALUE,...]]
    [--network=NETWORK; default="default"] [--preemptible]
    [--queue-count=QUEUE_COUNT] [--range=RANGE] [--reserved]
    [--scopes=[SCOPES,...]] [--service-account=SERVICE_ACCOUNT]
    [--shielded-secure-boot] [--spot] [--subnetwork=SUBNETWORK]
    [--tags=[TAGS,...]]
    [--accelerator-type=ACCELERATOR_TYPE; default="v2-8"
      | --topology=TOPOLOGY --type=TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tpu resource - Name of the Cloud TPU VM node to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument tpu on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TPU
     ID of the tpu or fully qualified identifier for the tpu.

     To set the tpu attribute:
     + provide the argument tpu on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument tpu on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | Runtime version for the TPU, such as 2.3. For a list of available versions run: gcloud compute tpus tpu-vm versions list |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--boot-disk` | [KEY=VALUE,...] |  | Specifies the boot disk configuration. $ gcloud compute tpus tpu-vm create \ --boot-disk kms-key=<full_kms_key_name_here> The following keys are allowed: kms-key Specifies the fully qualified Cloud KMS cryptokey name which will be used to protect the disk. KMS cryptokey name format: projects/<kms-project>/locations/<kms-location>/keyRings/<kms-keyring>/cryptoKeys/<key-name> |
| `--data-disk` | [mode=MODE],[source=SOURCE] |  | Additional data disks for the TPU VM. This flag must be repeated to provide multiple data disks. For example: $ gcloud compute tpus tpu-vm create \ --data-disk \ source=projects/my-project/zones/us-central1-c/disks/my-disk,\ mode=read-only The following keys are allowed: source Specifies the full path to an existing disk. Required. The disk must be in the same zone. mode Specifies the mode in which to attach this disk. Valid options are 'read-write', 'read-only'. If not specified, the default is 'read-write'. |
| `--description` | DESCRIPTION |  | Text description of the TPU. |
| `--internal-ips` |  |  | Indicate that the IP addresses for the node should be internal. The default is that external IP addresses will be associated with the TPU workers. |
| `--labels` | [KEY=VALUE,...] |  | Resource labels to represent user-provided metadata. See https://cloud.google.com/compute/docs/labeling-resources for details. |
| `--metadata` | [KEY=VALUE,...] |  | List of comma-separated metadata key-value pairs for the Cloud TPU VM node. Example: --metadata='key1=value1,key2=value2' |
| `--metadata-from-file` | [KEY=VALUE,...] |  | Same as --metadata except the value for the entry will be read from a local file. Example: --metadata-from-file='key1=value1.txt' |
| `--network` | NETWORK | default | Network that this TPU will be a part of. |
| `--preemptible` |  |  | If provided, the TPU will be preemptible and time-limited. It may be preempted to free up resources for standard TPUs, and will only be able to run for a limited amount of time. Preemptible TPUs cannot be restarted. |
| `--queue-count` | QUEUE_COUNT |  | Specifies the networking queue count for TPU VM instances. Both Rx and Tx queues will be set to this number. If it's not specified, a default queue count will be assigned. For Virtio-net, each interface will get min(floor(#vCPU / #vNIC), 32) queues. For gVNIC, each interface will get min(floor(#vCPU / #vNIC / 2), 16) queues. |
| `--range` | RANGE |  | CIDR Range for the TPU. The IP range that the TPU will select an IP address from. Must be in CIDR notation and a /29 range, for example 192.168.0.0/29. Errors will occur if the CIDR range has already been used for a currently existing TPU, the CIDR range conflicts with any networks in the user's provided network, or the provided network is peered with another network that is using that CIDR range. |
| `--reserved` |  |  | When specified, will attempt to create the TPU node under reservations made in the current project. The reservations can be made separately but used in aggregated form. i.e., the user can make a reservation of 128 V2 TPUs and later on make another reservation of 128 V2 TPUs then creates a v2-256 TPU instance. If there exists no reservation or not sufficient amount of reserved cores under the project, the request will fail due to lack of capacity. |
| `--scopes` | [SCOPES,...] |  | List of comma-separated scopes to be made available for the service account. |
| `--service-account` | SERVICE_ACCOUNT |  | Email address of the service account. If empty, default Google Compute Engine service account will be used. |
| `--shielded-secure-boot` |  |  | Specifies that the TPU instances are created with secure boot enabled. This implicitly makes them Shielded VM instances. |
| `--spot` |  |  | If specified, create this VM as a spot VM. Spot VMs make unused capacity available at highly discounted rates. Spot VMs may be preempted at any time if the capacity is needed, but unless preempted there is no limit on runtime duration. Spot VM TPUs cannot be restarted, and must be recreated again. |
| `--subnetwork` | SUBNETWORK |  | Subnetwork that this TPU will be a part of. |
| `--tags` | [TAGS,...] |  | Tags to apply to the TPU Node. Tags are used to identify valid sources or targets for network firewalls. See https://cloud.google.com/vpc/docs/add-remove-network-tags for more details. |


**Examples:**
```bash
To create a TPU VM node with ID my-tpu in the default user project, network
and compute/zone (with other defaults supplied by API), run:

    $ gcloud compute tpus tpu-vm create my-tpu

To create a TPU VM node in a specific network, run:

    $ gcloud compute tpus tpu-vm create my-tpu --zone=us-central1-a \
        --network=my-tf-network --description='My TPU VM' \
        --version='v2-alpha'

To create a small TPU VM v2 pod, run:

    $ gcloud compute tpus tpu-vm create my-tpu --zone=us-central1-a \
        --accelerator-type='v2-32' --description='My TPU VM' \
        --version='v2-alpha'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/create)

---
### `gcloud compute tpus tpu-vm delete`

Delete a Cloud TPU VM node

Delete a Cloud TPU VM node.

**Synopsis:**
```
gcloud compute tpus tpu-vm delete (TPU : --zone=ZONE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tpu resource - Name of the Cloud TPU VM node to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument tpu on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TPU
     ID of the tpu or fully qualified identifier for the tpu.

     To set the tpu attribute:
     + provide the argument tpu on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument tpu on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a TPU VM with ID my-tpu in zone us-central1-b, run:

    $ gcloud compute tpus tpu-vm delete my-tpu --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/delete)

---
### `gcloud compute tpus tpu-vm describe`

Describe a Cloud TPU VM node

Describe a Cloud TPU VM node.

**Synopsis:**
```
gcloud compute tpus tpu-vm describe (TPU : --zone=ZONE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tpu resource - Name of the Cloud TPU VM node to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument tpu on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TPU
     ID of the tpu or fully qualified identifier for the tpu.

     To set the tpu attribute:
     + provide the argument tpu on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument tpu on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To describe a Cloud TPU VM node with ID my-tpu in zone us-central1-b, run:

    $ gcloud compute tpus tpu-vm describe my-tpu --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/describe)

---
### `gcloud compute tpus tpu-vm get-guest-attributes`

Retrieve the Guest Attributes for a Cloud TPU VM

Retrieve the Guest Attributes for a Cloud TPU VM.

**Synopsis:**
```
gcloud compute tpus tpu-vm get-guest-attributes (TPU : --zone=ZONE)
    [--query-path=QUERY_PATH] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tpu resource - Name of the Cloud TPU VM. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument tpu on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TPU
     ID of the tpu or fully qualified identifier for the tpu.

     To set the tpu attribute:
     + provide the argument tpu on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument tpu on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--query-path` | QUERY_PATH |  | Attribute path to query. Can be empty string or of the form <namespace>/ or <namespace>/<key>. Default is the empty string. |


**Examples:**
```bash
To retrieve the guest attributes, run:

    $ gcloud compute tpus tpu-vm get-guest-attributes my-tpu \
        --zone=us-central1-b

To select only a specific query path, use the --query-path flag:

    $ gcloud compute tpus tpu-vm get-guest-attributes my-tpu \
        --zone=us-central1-b --query-path=lifecycle/event

To only display the guest attributes for one of the workers in a TPU pod,
use the --filter flag:

    $ gcloud compute tpus tpu-vm get-guest-attributes my-tpu \
        --zone=us-central1-b --filter="worker_id:3"

where 3 is an example of the worker ID (0-indexed).
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/get-guest-attributes)

---
### `gcloud compute tpus tpu-vm list`

List Cloud TPU VM nodes

List Cloud TPU VM nodes.

**Synopsis:**
```
gcloud compute tpus tpu-vm list [--zone=ZONE] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the zone attribute: + provide the argument --zone on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list the Cloud TPU VM nodes in zone us-central1-b, run:

    $ gcloud compute tpus tpu-vm list --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/list)

---
### `gcloud compute tpus tpu-vm scp`

Copy files to and from a Cloud TPU VM via SCP

Copy files to and from a Cloud TPU VM via SCP.

**Synopsis:**
```
gcloud compute tpus tpu-vm scp [[USER@]INSTANCE:]SRC
    [[[USER@]INSTANCE:]SRC ...] [[USER@]INSTANCE:]DEST [--compress]
    [--dry-run] [--force-key-file-overwrite] [--internal-ip] [--plain]
    [--recurse] [--scp-flag=SCP_FLAG] [--ssh-key-file=SSH_KEY_FILE]
    [--strict-host-key-checking=STRICT_HOST_KEY_CHECKING]
    [--worker=WORKER; default="0"] [--zone=ZONE]
    [--ssh-key-expiration=SSH_KEY_EXPIRATION
      | --ssh-key-expire-after=SSH_KEY_EXPIRE_AFTER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[[USER@]INSTANCE:]SRC [[[USER@]INSTANCE:]SRC ...]
   Specifies the files to copy.

[[USER@]INSTANCE:]DEST
   Specifies a destination for the source files.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--compress` |  |  | Enable compression. |
| `--dry-run` |  |  | Print the equivalent scp/ssh command that would be run to stdout, instead of executing it. |
| `--force-key-file-overwrite` |  |  | If enabled, the gcloud command-line tool will regenerate and overwrite the files associated with a broken SSH key without asking for confirmation in both interactive and non-interactive environments. If disabled, the files associated with a broken SSH key will not be regenerated and will fail in both interactive and non-interactive environments. |
| `--internal-ip` |  |  | Connect to TPU VMs using their internal IP addresses rather than their external IP addresses. Use this to connect from a Google Compute Engine VM to a TPU VM on the same VPC network, or between two peered VPC networks. |
| `--plain` |  |  | Suppress the automatic addition of ssh(1)/scp(1) flags. This flag is useful if you want to take care of authentication yourself or use specific ssh/scp features. |
| `--recurse` |  |  | Upload directories recursively. |
| `--scp-flag` | SCP_FLAG |  | Additional flags to be passed to scp(1). This flag may be repeated. |
| `--ssh-key-file` | SSH_KEY_FILE |  | The path to the SSH key file. By default, this is ~\.ssh\google_compute_engine. |
| `--strict-host-key-checking` | one of: yes, no, ask |  | Override the default behavior of StrictHostKeyChecking for the connection. By default, StrictHostKeyChecking is set to 'no' the first time you connect to an instance, and will be set to 'yes' for all subsequent connections. STRICT_HOST_KEY_CHECKING must be one of: yes, no, ask. |
| `--worker` | WORKER | 0 | TPU worker to connect to. The supported value is a single 0-based index of the worker in the case of a TPU Pod. When also using the --command flag, it additionally supports a comma-separated list (e.g. '1,4,6'), range (e.g. '1-3'), or special keyword ``all" to run the command concurrently on each of the specified workers. Note that when targeting multiple workers, you should run 'ssh-add' with your private key prior to executing the gcloud command. Default: 'ssh-add ~/.ssh/google_compute_engine'. |
| `--zone` | ZONE |  | Zone of the tpu to scp. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To copy a file (for example, a text file in the local home directory) to a
Cloud TPU VM, run:

    $ gcloud compute tpus tpu-vm scp ~/my-file my-tpu:

To copy a file into all workers in a Cloud TPU VM, run:

    $ gcloud compute tpus tpu-vm scp ~/my-file my-tpu: --worker=all

To copy a file from a Cloud TPU VM to the home directory of the local
computer, run:

    $ gcloud compute tpus tpu-vm scp my-tpu:~/my-file ~/

To copy all files in a folder to a Cloud TPU VM, run:

    $ gcloud compute tpus tpu-vm scp ~/my-folder/ my-tpu: --recurse
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/scp)

---
### `gcloud compute tpus tpu-vm ssh`

SSH into a Cloud TPU VM

SSH into a Cloud TPU VM.

**Synopsis:**
```
gcloud compute tpus tpu-vm ssh [USER@]TPU [--dry-run]
    [--force-key-file-overwrite] [--internal-ip] [--plain]
    [--ssh-flag=SSH_FLAG] [--ssh-key-file=SSH_KEY_FILE]
    [--strict-host-key-checking=STRICT_HOST_KEY_CHECKING]
    [--worker=WORKER; default="0"] [--zone=ZONE]
    [--command=COMMAND --output-directory=OUTPUT_DIRECTORY]
    [--ssh-key-expiration=SSH_KEY_EXPIRATION
      | --ssh-key-expire-after=SSH_KEY_EXPIRE_AFTER] [GCLOUD_WIDE_FLAG ...]
    [-- SSH_ARGS ...]
```

**Positional arguments:**
```
[USER@]TPU
   Specifies the Cloud TPU VM to SSH into.

   USER specifies the username with which to SSH. If omitted, the user
   login name is used.

   TPU specifies the name of the Cloud TPU VM to SSH into.

[-- SSH_ARGS ...]
   Flags and positionals passed to the underlying ssh implementation.

   The '--' argument must be specified between gcloud specific args on the
   left and SSH_ARGS on the right. Example:

       $ gcloud compute tpus tpu-vm ssh example-instance \
       --zone=us-central1-a -- -vvv -L 80:%TPU%:80
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dry-run` |  |  | Print the equivalent scp/ssh command that would be run to stdout, instead of executing it. |
| `--force-key-file-overwrite` |  |  | If enabled, the gcloud command-line tool will regenerate and overwrite the files associated with a broken SSH key without asking for confirmation in both interactive and non-interactive environments. If disabled, the files associated with a broken SSH key will not be regenerated and will fail in both interactive and non-interactive environments. |
| `--internal-ip` |  |  | Connect to TPU VMs using their internal IP addresses rather than their external IP addresses. Use this to connect from a Google Compute Engine VM to a TPU VM on the same VPC network, or between two peered VPC networks. |
| `--plain` |  |  | Suppress the automatic addition of ssh(1)/scp(1) flags. This flag is useful if you want to take care of authentication yourself or use specific ssh/scp features. |
| `--ssh-flag` | SSH_FLAG |  | Additional flags to be passed to ssh(1). It is recommended that flags be passed using an assignment operator and quotes. Example: $ gcloud compute tpus tpu-vm ssh example-instance \ --zone=us-central1-a --ssh-flag="-vvv" \ --ssh-flag="-L 80:localhost:80" This flag will replace occurences of %USER% and %TPU% with their dereferenced values. For example, passing ``80:%TPU%:80`` into the flag is equivalent to passing 80:162.222.181.197:80 to ssh(1) if the external IP address of 'example-instance' is 162.222.181.197. If connecting to the instance's external IP, then %TPU% is replaced with that, otherwise it is replaced with the internal IP. |
| `--ssh-key-file` | SSH_KEY_FILE |  | The path to the SSH key file. By default, this is ~\.ssh\google_compute_engine. |
| `--strict-host-key-checking` | one of: yes, no, ask |  | Override the default behavior of StrictHostKeyChecking for the connection. By default, StrictHostKeyChecking is set to 'no' the first time you connect to an instance, and will be set to 'yes' for all subsequent connections. STRICT_HOST_KEY_CHECKING must be one of: yes, no, ask. |
| `--worker` | WORKER | 0 | TPU worker to connect to. The supported value is a single 0-based index of the worker in the case of a TPU Pod. When also using the --command flag, it additionally supports a comma-separated list (e.g. '1,4,6'), range (e.g. '1-3'), or special keyword ``all" to run the command concurrently on each of the specified workers. Note that when targeting multiple workers, you should run 'ssh-add' with your private key prior to executing the gcloud command. Default: 'ssh-add ~/.ssh/google_compute_engine'. |
| `--zone` | ZONE |  | Zone of the tpu to ssh. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To SSH into a Cloud TPU VM, run:

    $ gcloud compute tpus tpu-vm ssh my-tpu

To SSH into worker 1 on a Cloud TPU VM Pod, run:

    $ gcloud compute tpus tpu-vm ssh my-tpu --worker=1

To run an SSH command in a Cloud TPU VM (for example, to print the time
since last boot), run:

    $ gcloud compute tpus tpu-vm ssh my-tpu --command="last boot"

To run the same command in all workers in a Cloud TPU VM simultaneously,
run:

    $ gcloud compute tpus tpu-vm ssh my-tpu --command="last boot" \
      --worker=all
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/ssh)

---
### `gcloud compute tpus tpu-vm start`

Start a Cloud TPU VM node

Start a Cloud TPU VM node.

**Synopsis:**
```
gcloud compute tpus tpu-vm start (TPU : --zone=ZONE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tpu resource - Name of the Cloud TPU VM node to start. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument tpu on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TPU
     ID of the tpu or fully qualified identifier for the tpu.

     To set the tpu attribute:
     + provide the argument tpu on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument tpu on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To start a Cloud TPU VM node with ID my-tpu in zone us-central1-b, run:

    $ gcloud compute tpus tpu-vm start my-tpu --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/start)

---
### `gcloud compute tpus tpu-vm stop`

Stop a Cloud TPU VM node

Stop a Cloud TPU VM node.

**Synopsis:**
```
gcloud compute tpus tpu-vm stop (TPU : --zone=ZONE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tpu resource - Name of the Cloud TPU VM node to stop. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument tpu on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TPU
     ID of the tpu or fully qualified identifier for the tpu.

     To set the tpu attribute:
     + provide the argument tpu on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument tpu on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To stop a Cloud TPU VM node with ID my-tpu in zone us-central1-b, run:

    $ gcloud compute tpus tpu-vm stop my-tpu --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/stop)

---
### `gcloud compute tpus tpu-vm update`

Update a Cloud TPU VM node

Update a Cloud TPU VM node.

**Synopsis:**
```
gcloud compute tpus tpu-vm update (TPU : --zone=ZONE)
    [--add-tags=[TAGS,...]] [--async] [--description=DESCRIPTION]
    [--internal-ips] [--update-labels=[KEY=VALUE,...]]
    [--attach-disk=[SOURCE=DATA_DISK,...] | --detach-disk=DATA_DISK]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--clear-tags | --remove-tags=[TAG,...]]
    [--metadata-from-file=[KEY=VALUE,...]
      | --update-metadata=[KEY=VALUE,...] --clear-metadata
      | --remove-metadata=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tpu resource - Name of the Cloud TPU VM node to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument tpu on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TPU
     ID of the tpu or fully qualified identifier for the tpu.

     To set the tpu attribute:
     + provide the argument tpu on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument tpu on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--add-tags` | [TAGS,...] |  | Tags to add to the TPU Node. Tags are used to identify valid sources or targets for network firewalls. See https://cloud.google.com/vpc/docs/add-remove-network-tags for more details. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Text description of the TPU. |
| `--internal-ips` |  |  | Indicate that the IP addresses for the node should be internal. The default is that external IP addresses will be associated with the TPU workers. |
| `--update-labels` | [KEY=VALUE,...] |  | Resource labels to update that represent user-provided metadata. If a label exists, its value is modified. Otherwise, a new label is created. See https://cloud.google.com/compute/docs/labeling-resources for details. |


**Examples:**
```bash
To modify a TPU VM node with ID my-tpu in the default user project and
compute/zone by updating the description to "A new description", run:

    $ gcloud compute tpus tpu-vm update my-tpu \
        --description="A new description"

To modify a TPU VM node with ID my-tpu in the default user project, network
and compute/zone (with other defaults supplied by API) by adding labels k0,
with value value0 and label k1 with value value1 and removing labels with
key k2, run:

    $ gcloud compute tpus tpu-vm update my-tpu \
        --update-labels=k0=value0,k1=value1 --remove-labels=k2

Labels can be used to identify the TPU VM node. To list TPU VM nodes with
the k1:value1 label, run:

    $ gcloud compute tpus tpu-vm list --filter='labels.k1=value1'

To list only the labels when describing a resource, use --format to filter
the result:

    $ gcloud compute tpus tpu-vm describe my-tpu \
        --format="default(labels)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/update)

---

## `gcloud compute tpus tpu-vm accelerator-types` — list or Describe Available Cloud TPU VM node accelerator types
### `gcloud compute tpus tpu-vm accelerator-types describe`

Describe an accelerator type available for Cloud TPU VM nodes

Get details on an accelerator type.

**Synopsis:**
```
gcloud compute tpus tpu-vm accelerator-types describe
    (ACCELERATOR_TYPE : --zone=ZONE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Accelerator type resource - Name of the accelerator type to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument accelerator_type on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ACCELERATOR_TYPE
     ID of the accelerator_type or fully qualified identifier for the
     accelerator_type.

     To set the accelerator_type attribute:
     + provide the argument accelerator_type on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument accelerator_type on the command line with a
       fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To describe the v3-8 accelerator type in zone us-central1-b, run:

    $ gcloud compute tpus tpu-vm accelerator-types describe v3-8 \
        --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/accelerator-types/describe)

---
### `gcloud compute tpus tpu-vm accelerator-types list`

List available accelerator types for Cloud TPU VM nodes

List available accelerator types for for Cloud TPU VM nodes.

**Synopsis:**
```
gcloud compute tpus tpu-vm accelerator-types list [--zone=ZONE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the zone attribute: + provide the argument --zone on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list all of the accelerator types available in zone us-central1-b, run:

    $ gcloud compute tpus tpu-vm accelerator-types list \
        --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/accelerator-types/list)

---

## `gcloud compute tpus tpu-vm service-identity` — commands for Cloud TPU VM service identity
### `gcloud compute tpus tpu-vm service-identity create`

Create a Cloud TPU VM service identity for a project

Create a Cloud TPU VM service identity for a project.

The Cloud TPU VM creates a service identity (Google-owned service account)
for management of resources when the first Cloud TPU VM is created in a
project after TPU service activation. However, there are cases where the
service identity may need to be created beforehand to grant specific IAM
permissions to it, like access to a Google Cloud Storage bucket. This
method generates the service account without need to first create a Cloud
TPU VM.

This command generates a service identity valid for Cloud TPU VMs across
all zones in a project. The zone is required (either set in the gcloud
config defaults, as an environment variable, or --zone flag), but the
service identity generated will work across all Cloud TPU VM zones.

**Synopsis:**
```
gcloud compute tpus tpu-vm service-identity create [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the zone attribute: + provide the argument --zone on the command line; + set the property compute/zone. |


**Examples:**
```bash
To generate a Cloud TPU VM service identity for a project (using zone
europe-west4-a), run:

    $ gcloud compute tpus tpu-vm service-identity create \
        --zone=europe-west4-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/service-identity/create)

---

## `gcloud compute tpus tpu-vm versions` — explore available runtime versions for Cloud TPU VM nodes
### `gcloud compute tpus tpu-vm versions describe`

Describe a runtime version available for Cloud TPU VM nodes

Get details on a runtime version.

**Synopsis:**
```
gcloud compute tpus tpu-vm versions describe (VERSION : --zone=ZONE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime version resource - Name of the runtime version to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument version on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the runtime_version or fully qualified identifier for the
     runtime_version.

     To set the version attribute:
     + provide the argument version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To describe the TensorFlow 1.15 runtime version in zone us-central1-b, run:

    $ gcloud compute tpus tpu-vm versions describe 1.15 \
        --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/versions/describe)

---
### `gcloud compute tpus tpu-vm versions list`

List available runtime versions for Cloud TPU VM nodes

List runtime versions available for Cloud TPU VM nodes.

**Synopsis:**
```
gcloud compute tpus tpu-vm versions list [--zone=ZONE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the zone attribute: + provide the argument --zone on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list all of the runtime versions available in zone us-central1-b, run:

    $ gcloud compute tpus tpu-vm versions list --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/tpu-vm/versions/list)

---

## `gcloud compute tpus versions` — explore Available Tensorflow versions for Cloud TPUs
### `gcloud compute tpus versions describe`

Describe a Tensorflow version available for Cloud TPUs

Get details on a Tensorflow version.

To get a list of available Tesnorflow versions for your location run:

    $ gcloud compute tpus versions list

**Synopsis:**
```
gcloud compute tpus versions describe (VERSION : --zone=ZONE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tensorflow version resource - The Tensorflow version you want to describe.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument version on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the tensorflow_version or fully qualified identifier for the
     tensorflow_version.

     To set the version attribute:
     + provide the argument version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The compute/zone of the Cloud TPU.

     If not specified, will use default compute/zone.

     To set the zone attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
The following command describes the TensorFlow 1.15 version running in zone
us-central1-b:

    $ gcloud compute tpus versions describe 1.15 --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/versions/describe)

---
### `gcloud compute tpus versions list`

List available Tensorflow versions

List Tensorflow versions available for Cloud TPUs.

**Synopsis:**
```
gcloud compute tpus versions list [--zone=ZONE] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the zone attribute: + provide the argument --zone on the command line; + set the property compute/zone. |


**Examples:**
```bash
The following command lists all of the TensorFlow versions available in
zone us-central1-b:

    $ gcloud compute tpus versions list --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/tpus/versions/list)

---