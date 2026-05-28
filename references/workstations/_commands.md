# gcloud workstations (top-level commands)

### `gcloud workstations create`

Create a workstation

Create a workstation.

**Synopsis:**
```
gcloud workstations create
    (WORKSTATION : --cluster=CLUSTER --config=CONFIG --region=REGION)
    [--async] [--env=[KEY=VALUE,...]] [--labels=[KEY=VALUE,...]]
    [--source-workstation=SOURCE_WORKSTATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workstation resource - Arguments and flags that specify the workstation to
create. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument workstation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKSTATION
     ID of the workstation or fully qualified identifier for the
     workstation.

     To set the workstation attribute:
     + provide the argument workstation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The name of the cluster containing the workstation.

     To set the cluster attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --config=CONFIG
     The name of the config containing the workstation.

     To set the config attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --config on the command line;
     + set the property workstations/config.

  --region=REGION
     The name of the region of the workstation.

     To set the region attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--env` | [KEY=VALUE,...] |  | Environment variables passed to the Workstation. |
| `--labels` | [KEY=VALUE,...] |  | Labels that are applied to the workstation and propagated to the underlying Compute Engine resources. |
| `--source-workstation` | SOURCE_WORKSTATION |  | Source workstation from which this workstations persistent directories are cloned on creation. When specified, the workstations service agent must have compute.disks.createSnapshot and compute.snapshots.useReadOnly permissions on the source workstation's host project. |


**Examples:**
```bash
To create a workstation, run:

    $ gcloud workstations create WORKSTATION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/create)

---
### `gcloud workstations delete`

Delete a workstation

Delete a workstation.

**Synopsis:**
```
gcloud workstations delete
    (WORKSTATION : --cluster=CLUSTER --config=CONFIG --region=REGION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workstation resource - The name of the workstation to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument workstation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKSTATION
     ID of the workstation or fully qualified identifier for the
     workstation.

     To set the workstation attribute:
     + provide the argument workstation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The name of the cluster containing the workstation.

     To set the cluster attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --config=CONFIG
     The name of the config containing the workstation.

     To set the config attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --config on the command line;
     + set the property workstations/config.

  --region=REGION
     The name of the region of the workstation.

     To set the region attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a workstation, run:

    $ gcloud workstations delete WORKSTATION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/delete)

---
### `gcloud workstations describe`

Describe a workstation

Describe a workstation.

**Synopsis:**
```
gcloud workstations describe
    (WORKSTATION : --cluster=CLUSTER --config=CONFIG --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workstation resource - The name of the workstation to display. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument workstation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKSTATION
     ID of the workstation or fully qualified identifier for the
     workstation.

     To set the workstation attribute:
     + provide the argument workstation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The name of the cluster containing the workstation.

     To set the cluster attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --config=CONFIG
     The name of the config containing the workstation.

     To set the config attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --config on the command line;
     + set the property workstations/config.

  --region=REGION
     The name of the region of the workstation.

     To set the region attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.
```

**Examples:**
```bash
To describe a workstation, run:

    $ gcloud workstations describe WORKSTATION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/describe)

---
### `gcloud workstations get-iam-policy`

Get the IAM policy for a workstation

gcloud workstations get-iam-policy displays the IAM policy associated with
a given workstation. If formatted as JSON, the output can be edited and
used as a policy file for set-iam-policy. The output includes an "etag"
field identifying the version emitted and allowing detection of concurrent
policy updates; see $ {parent} set-iam-policy for additional details.

**Synopsis:**
```
gcloud workstations get-iam-policy
    (WORKSTATION : --cluster=CLUSTER --config=CONFIG --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workstation resource - The workstation for which to display the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument workstation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKSTATION
     ID of the workstation or fully qualified identifier for the
     workstation.

     To set the workstation attribute:
     + provide the argument workstation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The name of the cluster containing the workstation.

     To set the cluster attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --config=CONFIG
     The name of the config containing the workstation.

     To set the config attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --config on the command line;
     + set the property workstations/config.

  --region=REGION
     The name of the region of the workstation.

     To set the region attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.
```

**Examples:**
```bash
To get the IAM policy for a given workstation, run:

    $ gcloud workstations get-iam-policy WORKSTATION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/get-iam-policy)

---
### `gcloud workstations list`

List workstations

List all workstations under the specified configuration.

**Synopsis:**
```
gcloud workstations list
    [--cluster=CLUSTER --config=CONFIG --region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[* set the property core/project.]_ The name of the cluster containing the config. To set the cluster attribute: + provide the argument --config on the command line with a fully specified name; + set the property workstations/config with a fully specified name; + default is all configs with a fully specified name; + provide the argument --cluster on the command line; + set the property workstations/cluster; + default is all clusters . |
| `--config` | CONFIG |  | _[* set the property core/project.]_ ID of the config or fully qualified identifier for the config. To set the config attribute: + provide the argument --config on the command line; + set the property workstations/config; + default is all configs . |
| `--region` | REGION |  | _[* set the property core/project.]_ The name of the region of the config. To set the region attribute: + provide the argument --config on the command line with a fully specified name; + set the property workstations/config with a fully specified name; + default is all configs with a fully specified name; + provide the argument --region on the command line; + set the property workstations/region; + default is all regions . |


**Examples:**
```bash
To list workstations, run:

    $ gcloud workstations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/list)

---
### `gcloud workstations list-usable`

List usable workstations

List all usable workstations under the specified configuration.

**Synopsis:**
```
gcloud workstations list-usable
    [--cluster=CLUSTER --config=CONFIG --region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[* set the property core/project.]_ The cluster for the config. To set the cluster attribute: + provide the argument --config on the command line with a fully specified name; + default is all configs with a fully specified name; + provide the argument --cluster on the command line; + set the property workstations/cluster; + default is all clusters. |
| `--config` | CONFIG |  | _[* set the property core/project.]_ ID of the config or fully qualified identifier for the config. To set the config attribute: + provide the argument --config on the command line; + default is all configs. |
| `--region` | REGION |  | _[* set the property core/project.]_ The region for the config. To set the region attribute: + provide the argument --config on the command line with a fully specified name; + default is all configs with a fully specified name; + provide the argument --region on the command line; + set the property workstations/region; + default is all regions. |


**Examples:**
```bash
To list usable workstations, run

    $ gcloud workstations list-usable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/list-usable)

---
### `gcloud workstations set-iam-policy`

Set the IAM policy for a workstation

Sets the IAM policy for the given workstation as defined in a JSON or YAML
file.

**Synopsis:**
```
gcloud workstations set-iam-policy
    (WORKSTATION : --cluster=CLUSTER --config=CONFIG --region=REGION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workstation resource - The workstation for which to display the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument workstation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKSTATION
     ID of the workstation or fully qualified identifier for the
     workstation.

     To set the workstation attribute:
     + provide the argument workstation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The name of the cluster containing the workstation.

     To set the cluster attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --config=CONFIG
     The name of the config containing the workstation.

     To set the config attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --config on the command line;
     + set the property workstations/config.

  --region=REGION
     The name of the region of the workstation.

     To set the region attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for the given workstation:

    $ gcloud workstations set-iam-policy WORKSTATION policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/set-iam-policy)

---
### `gcloud workstations ssh`

SSH into a running workstation

SSH into a running workstation.

Note that arguments for the NO_PROXY environment variable must be FQDNs.

**Synopsis:**
```
gcloud workstations ssh
    (WORKSTATION : --cluster=CLUSTER --config=CONFIG --region=REGION)
    [--command=COMMAND]
    [--local-host-port=LOCAL_HOST_PORT; default="localhost:0"]
    [--port=PORT; default=22] [--ssh-flag=SSH_FLAG]
    [--user=USER; default="user"] [GCLOUD_WIDE_FLAG ...] [-- SSH_ARGS ...]
```

**Positional arguments:**
```
Workstation resource - The group of arguments defining a workstation The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument workstation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKSTATION
     ID of the workstation or fully qualified identifier for the
     workstation.

     To set the workstation attribute:
     + provide the argument workstation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster for the workstation.

     To set the cluster attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --config=CONFIG
     The config for the workstation.

     To set the config attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --config on the command line;
     + set the property workstations/config.

  --region=REGION
     The region for the workstation.

     To set the region attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.

[-- SSH_ARGS ...]
   Flags and positionals passed to the underlying ssh implementation.

   The '--' argument must be specified between gcloud specific args on the
   left and SSH_ARGS on the right.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--command` | COMMAND |  | A command to run on the workstation. Runs the command on the target workstation and then exits. |
| `--local-host-port` | LOCAL_HOST_PORT | localhost:0 | LOCAL_HOST:LOCAL_PORT on which gcloud should bind and listen for connections that should be tunneled. LOCAL_PORT may be omitted, in which case it is treated as 0 and an arbitrary unused local port is chosen. The colon also may be omitted in that case. If LOCAL_PORT is 0, an arbitrary unused local port is chosen. |
| `--port` | PORT | 22 | The port on the workstation to which traffic should be sent. |
| `--ssh-flag` | SSH_FLAG |  | Additional flags to be passed to ssh(1). It is recommended that flags be passed using an assignment operator and quotes. Example: $ gcloud workstations ssh --ssh-flag="-vvv" \ --ssh-flag="-L 80:localhost:80" |
| `--user` | USER | user | The username with which to SSH. |


**Examples:**
```bash
To ssh into a running workstation, run:

    $ gcloud workstations ssh WORKSTATION

To specify the workstation port, run:

    $ gcloud workstations ssh WORKSTATION --port=22

To ssh into a running workstation with a username, run:

    $ gcloud workstations ssh WORKSTATION --user=my-user

To run a command on the workstation, such as getting a snapshot of the
guest's process tree, run:        $ gcloud workstations ssh WORKSTATION --command="ps -ejH"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/ssh)

---
### `gcloud workstations start`

Start a workstation

Start a workstation.

**Synopsis:**
```
gcloud workstations start
    (WORKSTATION : --cluster=CLUSTER --config=CONFIG --region=REGION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workstation resource - The group of arguments defining a workstation The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument workstation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKSTATION
     ID of the workstation or fully qualified identifier for the
     workstation.

     To set the workstation attribute:
     + provide the argument workstation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster for the workstation.

     To set the cluster attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --config=CONFIG
     The config for the workstation.

     To set the config attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --config on the command line;
     + set the property workstations/config.

  --region=REGION
     The region for the workstation.

     To set the region attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To start a workstation, run

    $ gcloud workstations start WORKSTATION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/start)

---
### `gcloud workstations start-tcp-tunnel`

Start a tunnel through which a local process can forward TCP traffic to the workstation

Start a tunnel through which a local process can forward TCP traffic to the
workstation.

Note that arguments for the NO_PROXY environment variable must be FQDNs.

**Synopsis:**
```
gcloud workstations start-tcp-tunnel
    (WORKSTATION : --cluster=CLUSTER --config=CONFIG --region=REGION)
    WORKSTATION_PORT
    [--local-host-port=LOCAL_HOST_PORT; default="localhost:0"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workstation resource - The group of arguments defining a workstation The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument workstation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKSTATION
     ID of the workstation or fully qualified identifier for the
     workstation.

     To set the workstation attribute:
     + provide the argument workstation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster for the workstation.

     To set the cluster attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --config=CONFIG
     The config for the workstation.

     To set the config attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --config on the command line;
     + set the property workstations/config.

  --region=REGION
     The region for the workstation.

     To set the region attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.

WORKSTATION_PORT
   The port on the workstation to which traffic should be sent.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--local-host-port` | LOCAL_HOST_PORT | localhost:0 | LOCAL_HOST:LOCAL_PORT on which gcloud should bind and listen for connections that should be tunneled. LOCAL_PORT may be omitted, in which case it is treated as 0 and an arbitrary unused local port is chosen. The colon also may be omitted in that case. If LOCAL_PORT is 0, an arbitrary unused local port is chosen. |


**Examples:**
```bash
To start a tunnel to port 22 on a workstation, run:

    $ gcloud workstations start-tcp-tunnel --project=my-project \
        --region=us-central1 --cluster=my-cluster --config=my-config \
        my-workstation 22
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/start-tcp-tunnel)

---
### `gcloud workstations stop`

Stop a workstation

Stop a workstation.

**Synopsis:**
```
gcloud workstations stop
    (WORKSTATION : --cluster=CLUSTER --config=CONFIG --region=REGION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workstation resource - The group of arguments defining a workstation The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument workstation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKSTATION
     ID of the workstation or fully qualified identifier for the
     workstation.

     To set the workstation attribute:
     + provide the argument workstation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster for the workstation.

     To set the cluster attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line;
     + set the property workstations/cluster.

  --config=CONFIG
     The config for the workstation.

     To set the config attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --config on the command line;
     + set the property workstations/config.

  --region=REGION
     The region for the workstation.

     To set the region attribute:
     + provide the argument workstation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To stop a workstation, run

    $ gcloud workstations stop WORKSTATION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/stop)

---