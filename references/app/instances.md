# gcloud app instances

view and manage your App Engine instances

### `gcloud app instances delete`

Delete a specified instance

Delete a specified instance.

**Synopsis:**
```
gcloud app instances delete INSTANCE --service=SERVICE, -s SERVICE
    --version=VERSION, -v VERSION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   The instance ID.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE, -s SERVICE |  | The service ID. |
| `--version` | VERSION, -v VERSION |  | The version ID. |


**Examples:**
```bash
To delete instance i1 of service s1 and version v1, run:

    $ gcloud app instances delete i1 --service=s1 --version=v1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/instances/delete)

---
### `gcloud app instances describe`

Display all data about an existing instance

Display all data about an existing instance.

**Synopsis:**
```
gcloud app instances describe INSTANCE --service=SERVICE, -s SERVICE
    --version=VERSION, -v VERSION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   The instance ID.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE, -s SERVICE |  | The service ID. |
| `--version` | VERSION, -v VERSION |  | The version ID. |


**Examples:**
```bash
To show all data about instance i1 for service s1 and version v1, run:

    $ gcloud app instances describe --service=s1 --version=v1 i1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/instances/describe)

---
### `gcloud app instances disable-debug`

Disable debug mode for an instance

When not in debug mode, SSH will be disabled on the VMs. They will be
included in the health checking pools.

Note that any local changes to an instance will be lost if debug mode is
disabled on the instance. New instance(s) may spawn depending on the app's
scaling settings.

**Synopsis:**
```
gcloud app instances disable-debug [INSTANCE]
    [--service=SERVICE, -s SERVICE] [--version=VERSION, -v VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[INSTANCE]
   The instance ID to disable debug mode on. If not specified, select
   instance interactively. Must uniquely specify (with other flags)
   exactly one instance
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE, -s SERVICE |  | If specified, only match instances belonging to the given service. This affects both interactive and non-interactive selection. |
| `--version` | VERSION, -v VERSION |  | If specified, only match instances belonging to the given version. This affects both interactive and non-interactive selection. |


**Examples:**
```bash
To disable debug mode for a particular instance, run:

    $ gcloud app instances disable-debug --service=s1 --version=v1 i1

To disable debug mode for an instance chosen interactively, run:

    $ gcloud app instances disable-debug
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/instances/disable-debug)

---
### `gcloud app instances enable-debug`

Enable debug mode for an instance (only works on the flexible environment)

When in debug mode, SSH will be enabled on the VMs, and you can use gcloud
compute ssh to login to them. They will be removed from the health checking
pools, but they still receive requests.

Note that any local changes to an instance will be lost if debug mode is
disabled on the instance. New instance(s) may spawn depending on the app's
scaling settings.

Additionally, debug mode doesn't work for applications using the App Engine
standard environment.

**Synopsis:**
```
gcloud app instances enable-debug [INSTANCE]
    [--service=SERVICE, -s SERVICE] [--version=VERSION, -v VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[INSTANCE]
   Instance ID to enable debug mode on. If not specified, select instance
   interactively. Must uniquely specify (with other flags) exactly one
   instance
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE, -s SERVICE |  | If specified, only match instances belonging to the given service. This affects both interactive and non-interactive selection. |
| `--version` | VERSION, -v VERSION |  | If specified, only match instances belonging to the given version. This affects both interactive and non-interactive selection. |


**Examples:**
```bash
To enable debug mode for a particular instance, run:

    $ gcloud app instances enable-debug --service=s1 --version=v1 i1

To enable debug mode for an instance chosen interactively, run:

    $ gcloud app instances enable-debug
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/instances/enable-debug)

---
### `gcloud app instances list`

List the instances affiliated with the current App Engine project

List the instances affiliated with the current App Engine project.

**Synopsis:**
```
gcloud app instances list [--service=SERVICE, -s SERVICE]
    [--version=VERSION, -v VERSION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE, -s SERVICE |  | If specified, only list instances belonging to the given service. |
| `--version` | VERSION, -v VERSION |  | If specified, only list instances belonging to the given version. |


**Examples:**
```bash
To list all App Engine instances, run:

    $ gcloud app instances list

To list all App Engine instances for a given service, run:

    $ gcloud app instances list -s myservice

To list all App Engine instances for a given version, run:

    $ gcloud app instances list -v v1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/instances/list)

---
### `gcloud app instances scp`

SCP from or to the VM of an App Engine Flexible instance

gcloud app instances scp lets you remotely copy files to or from an App
Engine Flexible instance.

gcloud app instances scp resolves the instance's IP address and
pre-populates the VM with a public key managed by gcloud. If the gcloud
managed key pair does not exist, it is generated the first time an SSH
command is run, which may prompt you for a passphrase for the private key
encryption.

All SSH commands require the OpenSSH client suite to be installed on Linux
and Mac OS X. On Windows, the Google Cloud CLI comes with a bundled PuTTY
suite instead, so it has no external dependencies.

**Synopsis:**
```
gcloud app instances scp [INSTANCE:]SRC [[INSTANCE:]SRC ...]
    [INSTANCE:]DEST [--compress] [--recurse] [--service=SERVICE]
    [--tunnel-through-iap] [--version=VERSION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[INSTANCE:]SRC [[INSTANCE:]SRC ...]
   Specifies the files to copy.

[INSTANCE:]DEST
   Specifies a destination for the source files.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--compress` |  |  | Enable compression. |
| `--recurse` |  |  | Upload directories recursively. |
| `--service` | SERVICE |  | The service ID. |
| `--tunnel-through-iap` |  |  | Tunnel the ssh connection through Identity-Aware Proxy for TCP forwarding. To learn more, see the IAP for TCP forwarding documentation (https://cloud.google.com/iap/docs/tcp-forwarding-overview). |
| `--version` | VERSION |  | The version ID. |


**Examples:**
```bash
To copy one file from a remote instance to the local machine, run:

    $ gcloud app instances scp --service=s1 --version=v1 \
      i1:remote_file local_file

To copy several local files to a remote instance, run:

    $ gcloud app instances scp --service=s1 --version=v1 local_1 \
      local_1 i1:remote_dir

To use recursive copy, run:

    $ gcloud app instances scp --service=s1 --version=v1 \
      --recurse local_dir i1:remote_dir
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/instances/scp)

---
### `gcloud app instances ssh`

SSH into the VM of an App Engine Flexible instance

gcloud app instances ssh lets you remotely log in to your running App
Engine Flexible instances under two conditions:
  o The instance is running.
  o The instance has an external IP address. To check from the Cloud
    Console, go to the Instances page and confirm that there is an IP
    address listed in the VM IP column. To check from your app.yaml, open
    your app.yaml and look at the network settings. The instance_ip_mode
    field must be either not listed or set to external.

gcloud app instances ssh resolves the instance's IP address and
pre-populates the VM with a public key managed by gcloud. If the gcloud
managed key pair does not exist, it is generated the first time an SSH
command is run, which may prompt you for a passphrase for the private key
encryption.

All SSH commands require the OpenSSH client suite to be installed on Linux
and Mac OS X. On Windows, the Google Cloud CLI comes with a bundled PuTTY
suite instead, so it has no external dependencies.

**Synopsis:**
```
gcloud app instances ssh INSTANCE [--container=CONTAINER]
    [--service=SERVICE] [--tunnel-through-iap] [--version=VERSION]
    [GCLOUD_WIDE_FLAG ...] [-- COMMAND ...]
```

**Positional arguments:**
```
INSTANCE
   The instance ID.

[-- COMMAND ...]
   Remote command to execute on the VM.

   The '--' argument must be specified between gcloud specific args on the
   left and COMMAND on the right.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--container` | CONTAINER |  | Name of the container within the VM to connect to. |
| `--service` | SERVICE |  | The service ID. |
| `--tunnel-through-iap` |  |  | Tunnel the ssh connection through Identity-Aware Proxy for TCP forwarding. To learn more, see the IAP for TCP forwarding documentation (https://cloud.google.com/iap/docs/tcp-forwarding-overview). |
| `--version` | VERSION |  | The version ID. |


**Examples:**
```bash
To SSH into an App Engine Flexible instance, run:

    $ gcloud app instances ssh --service=s1 --version=v1 i1

To SSH into the app container within an instance, run:

    $ gcloud app instances ssh --service=s1 --version=v1 i1 \
      --container=gaeapp

To SSH into the app container and run a remote command, run:

    $ gcloud app instances ssh --service=s1 --version=v1 i1 \
      --container=gaeapp -- echo hello
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/instances/ssh)

---