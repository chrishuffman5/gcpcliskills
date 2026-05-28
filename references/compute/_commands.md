# gcloud compute (top-level commands)

### `gcloud compute config-ssh`

Populate SSH config files with Host entries from each instance

gcloud compute config-ssh makes SSHing to virtual machine instances easier
by adding an alias for each instance to the user SSH configuration
(~/.ssh/config) file.

In most cases, it is sufficient to run:

    $ gcloud compute config-ssh

Each instance will be given an alias of the form NAME.ZONE.PROJECT. For
example, if example-instance resides in us-central1-a, you can SSH to it by
running:

    $ ssh example-instance.us-central1-a.MY-PROJECT

On some platforms, the host alias can be tab-completed, making the long
alias less daunting to type.

The aliases created interface with SSH-based programs like scp(1), so it is
possible to use the aliases elsewhere:

    $ scp ~/MY-FILE example-instance.us-central1-a.MY-PROJECT:~

Whenever instances are added, removed, or their external IP addresses are
changed, the remove command must be run to clear the existing configuration
and then the command can set executed to set the configuration to the
current state.

This command ensures that the user's public SSH key is present in the
project's metadata. If the user does not have a public SSH key, one is
generated using ssh-keygen(1) (if the --quiet flag is given, the generated
key will have an empty passphrase).

**Synopsis:**
```
gcloud compute config-ssh [--dry-run] [--force-key-file-overwrite]
    [--remove] [--ssh-config-file=SSH_CONFIG_FILE]
    [--ssh-key-file=SSH_KEY_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dry-run` |  |  | If provided, the proposed changes to the SSH config file are printed to standard output and no actual changes are made. |
| `--force-key-file-overwrite` |  |  | If enabled, the gcloud command-line tool will regenerate and overwrite the files associated with a broken SSH key without asking for confirmation in both interactive and non-interactive environments. If disabled, the files associated with a broken SSH key will not be regenerated and will fail in both interactive and non-interactive environments. |
| `--remove` |  |  | If provided, any changes made to the SSH config file by this tool are reverted. |
| `--ssh-config-file` | SSH_CONFIG_FILE |  | Specifies an alternative per-user SSH configuration file. By default, this is ~\.ssh\config. |
| `--ssh-key-file` | SSH_KEY_FILE |  | The path to the SSH key file. By default, this is ~\.ssh\google_compute_engine. |


**Examples:**
```bash
To populate SSH config file with Host entries from each running instance,
run:

    $ gcloud compute config-ssh

To remove the change to the SSH config file by this command, run:

    $ gcloud compute config-ssh --remove
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/config-ssh)

---
### `gcloud compute connect-to-serial-port`

Connect to the serial port of an instance

gcloud compute connect-to-serial-port allows users to connect to, and
interact with, a VM's virtual serial port using ssh as the secure,
authenticated transport protocol.

The user must first enable serial port access to a given VM by setting the
'serial-port-enable=true' metadata key-value pair. Setting
'serial-port-enable' on the project-level metadata enables serial port
access to all VMs in the project.

This command uses the same SSH key pair as the gcloud compute ssh command
and also ensures that the user's public SSH key is present in the project's
metadata. If the user does not have a public SSH key, one is generated
using ssh-keygen.

**Synopsis:**
```
gcloud compute connect-to-serial-port [USER@]INSTANCE [--dry-run]
    [--extra-args=KEY=VALUE,[KEY=VALUE,...]] [--force-key-file-overwrite]
    [--location=LOCATION] [--port=PORT; default=1]
    [--ssh-key-file=SSH_KEY_FILE] [--zone=ZONE]
    [--ssh-key-expiration=SSH_KEY_EXPIRATION
      | --ssh-key-expire-after=SSH_KEY_EXPIRE_AFTER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[USER@]INSTANCE
   Specifies the user/instance for the serial port connection.

   USER specifies the username to authenticate as. If omitted, the current
   OS user is selected.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dry-run` |  |  | If provided, the ssh command is printed to standard out rather than being executed. |
| `--extra-args` | KEY=VALUE,[KEY=VALUE,...] |  | Optional arguments can be passed to the serial port connection by passing key-value pairs to this flag, such as max-connections=N or replay-lines=N. See https://cloud.google.com/compute/docs/instances/interacting-with-serial-console for additional options. |
| `--force-key-file-overwrite` |  |  | If enabled, the gcloud command-line tool will regenerate and overwrite the files associated with a broken SSH key without asking for confirmation in both interactive and non-interactive environments. If disabled, the files associated with a broken SSH key will not be regenerated and will fail in both interactive and non-interactive environments. |
| `--location` | LOCATION |  | If provided, the region in which the serial console connection will occur. Must be the region of the VM to connect to. |
| `--port` | PORT | 1 | The number of the requested serial port. Can be 1-4, default is 1. Instances can support up to four serial ports. By default, this command will connect to the first serial port. Setting this flag will connect to the requested serial port. |
| `--ssh-key-file` | SSH_KEY_FILE |  | The path to the SSH key file. By default, this is ~\.ssh\google_compute_engine. |
| `--zone` | ZONE |  | Zone of the instance to connect to. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To connect to the serial port of the instance 'my-instance' in zone
'us-central1-f', run:

    $ gcloud compute connect-to-serial-port my-instance \
        --zone=us-central1-f
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/connect-to-serial-port)

---
### `gcloud compute copy-files`

Copy files to and from Google Compute Engine virtual machines via scp

gcloud compute copy-files copies files between a virtual machine instance
and your local machine using the scp command. This command does not work
for Windows VMs.

To denote a remote file, prefix the file name with the virtual machine
instance name (e.g., example-instance:~/FILE). To denote a local file, do
not add a prefix to the file name (e.g., ~/FILE).

If a file contains a colon (``:''), you must specify it by either using an
absolute path or a path that begins with ``./''.

Under the covers, scp(1) or pscp (on Windows) is used to facilitate the
transfer.

When the destination is local, all sources must be the same virtual machine
instance. When the destination is remote, all sources must be local.

**Synopsis:**
```
gcloud compute copy-files [[USER@]INSTANCE:]SRC [[[USER@]INSTANCE:]SRC ...]
    [[USER@]INSTANCE:]DEST [--dry-run] [--force-key-file-overwrite]
    [--plain] [--ssh-key-file=SSH_KEY_FILE]
    [--strict-host-key-checking=STRICT_HOST_KEY_CHECKING] [--zone=ZONE]
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
| `--dry-run` |  |  | Print the equivalent scp/ssh command that would be run to stdout, instead of executing it. |
| `--force-key-file-overwrite` |  |  | If enabled, the gcloud command-line tool will regenerate and overwrite the files associated with a broken SSH key without asking for confirmation in both interactive and non-interactive environments. If disabled, the files associated with a broken SSH key will not be regenerated and will fail in both interactive and non-interactive environments. |
| `--plain` |  |  | Suppress the automatic addition of ssh(1)/scp(1) flags. This flag is useful if you want to take care of authentication yourself or use specific ssh/scp features. |
| `--ssh-key-file` | SSH_KEY_FILE |  | The path to the SSH key file. By default, this is ~\.ssh\google_compute_engine. |
| `--strict-host-key-checking` | one of: yes, no, ask |  | Override the default behavior of StrictHostKeyChecking for the connection. By default, StrictHostKeyChecking is set to 'no' the first time you connect to an instance, and will be set to 'yes' for all subsequent connections. STRICT_HOST_KEY_CHECKING must be one of: yes, no, ask. |
| `--zone` | ZONE |  | The zone of the instance to copy files to/from. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To copy a remote directory '~/REMOTE-DIR' on the instance of
'example-instance' to '~/LOCAL-DIR' on the local host, run:

    $ gcloud compute copy-files example-instance:~/REMOTE-DIR \
        ~/LOCAL-DIR --zone=us-central1-a

To copy files from your local host to a virtual machine, run:

    $ gcloud compute copy-files ~/LOCAL-FILE-1 ~/LOCAL-FILE-2 \
        example-instance:~/REMOTE-DIR --zone=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/copy-files)

---
### `gcloud compute reset-windows-password`

Reset and return a password for a Windows machine instance

gcloud compute reset-windows-password allows a user to reset and retrieve a
password for a Windows virtual machine instance. If the Windows account
does not exist, this command will cause the account to be created and the
password for that new account will be returned.

For Windows instances that are running a domain controller, running this
command creates a new domain user if the user does not exist, or resets the
password if the user does exist. It is not possible to use this command to
create a local user on a domain-controller instance.

NOTE: When resetting passwords or adding a new user to a Domain Controller
in this way, the user will be added to the built in Admin Group on the
Domain Controller. This will give the user wide reaching permissions. If
this is not the desired outcome then Active Directory Users and Computers
should be used instead.

For all other instances, including domain-joined instances, running this
command creates a local user or resets the password for a local user.

WARNING: Resetting a password for an existing user can cause the loss of
data encrypted with the current Windows password, such as encrypted files
or stored passwords.

The user running this command must have write permission for the Google
Compute Engine project containing the Windows instance.

**Synopsis:**
```
gcloud compute reset-windows-password INSTANCE_NAME [--user=USER]
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--user` | USER |  | USER specifies the username to get the password for. If omitted, the username is derived from your authenticated account email address. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To reset the password for user 'foo' on a Windows instance 'my-instance' in
zone 'us-central1-f', run:

    $ gcloud compute reset-windows-password my-instance \
        --zone=us-central1-f --user=foo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reset-windows-password)

---
### `gcloud compute scp`

Copy files to and from Google Compute Engine virtual machines via scp

gcloud compute scp securely copies files between a virtual machine instance
and your local machine using the scp command.

This command works for Linux VMs and Windows Server 2019 and later VMs that
have SSH enabled
(https://cloud.google.com/compute/docs/connect/windows-ssh).

In order to set up a successful transfer, follow these guidelines:
  o Prefix remote file names with the virtual machine instance name
    (e.g., example-instance:~/FILE).
  o Local file names can be used as is (e.g., ~/FILE).
  o File names containing a colon (``:'') must be invoked by either their
    absolute path or a path that begins with ``./''.
  o When the destination of your transfer is local, all source files must
    be from the same virtual machine.
  o When the destination of your transfer is remote instead, all sources
    must be local.
  o When the destination is Windows Server, the source must be using a
    similar SSH version.

Under the covers, scp(1) is used to facilitate the transfer.

If the --region and --network flags are provided, then --plain and
--tunnel-through-iap are implied and any remote file names must be prefixed
with the remote IP address instead of the instance name. This is most
useful for connecting to on-prem resources.

**Synopsis:**
```
gcloud compute scp [[USER@]INSTANCE:]SRC [[[USER@]INSTANCE:]SRC ...]
    [[USER@]INSTANCE:]DEST [--compress] [--dry-run]
    [--force-key-file-overwrite] [--plain] [--port=PORT] [--recurse]
    [--scp-flag=SCP_FLAG] [--ssh-key-file=SSH_KEY_FILE]
    [--strict-host-key-checking=STRICT_HOST_KEY_CHECKING] [--zone=ZONE]
    [--internal-ip | --tunnel-through-iap]
    [--network=NETWORK --region=REGION : --dest-group=DEST_GROUP]
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
| `--plain` |  |  | Suppress the automatic addition of ssh(1)/scp(1) flags. This flag is useful if you want to take care of authentication yourself or use specific ssh/scp features. |
| `--port` | PORT |  | The port to connect to. |
| `--recurse` |  |  | Upload directories recursively. |
| `--scp-flag` | SCP_FLAG |  | Extra flag to be sent to scp. This flag may be repeated. |
| `--ssh-key-file` | SSH_KEY_FILE |  | The path to the SSH key file. By default, this is ~\.ssh\google_compute_engine. |
| `--strict-host-key-checking` | one of: yes, no, ask |  | Override the default behavior of StrictHostKeyChecking for the connection. By default, StrictHostKeyChecking is set to 'no' the first time you connect to an instance, and will be set to 'yes' for all subsequent connections. STRICT_HOST_KEY_CHECKING must be one of: yes, no, ask. |
| `--zone` | ZONE |  | The zone of the instance to copy files to/from. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |
| `--network` | NETWORK |  | _[(https://cloud.google.com/iap/docs/tcp-forwarding-overview).]_ Configures the VPC network to use when connecting via IP address or FQDN. |
| `--region` | REGION |  | _[(https://cloud.google.com/iap/docs/tcp-forwarding-overview).]_ Configures the region to use when connecting via IP address or FQDN. |
| `--dest-group` | DEST_GROUP |  | _[(https://cloud.google.com/iap/docs/tcp-forwarding-overview).]_ Configures the destination group to use when connecting via IP address or FQDN. |


**Examples:**
```bash
To copy a remote directory, ~/narnia, from example-instance to the
~/wardrobe directory of your local host, run:

    $ gcloud compute scp --recurse example-instance:~/narnia ~/wardrobe

Conversely, files from your local computer can be copied to a virtual
machine:

    $ gcloud compute scp ~/localtest.txt ~/localtest2.txt \
        example-instance:~/narnia

Remote Windows-based virtual machines require you to provide a path using
backslash notation:

    $ gcloud compute scp ~/localtest.txt ~/localtest2.txt \
        example-windows-instance:"C:\Users\Public"

Paths for remote Windows-based virtual machines which contain spaces in
directory name should be appropriately protected with a pair of nested
single and double quotes:

    $ gcloud compute scp ~/localtest.txt \
        'example-windows-instance:"C:\Users\Public\Test Folder"'

If the zone cannot be determined, you will be prompted for it. Use the
--zone flag to avoid being prompted:

    $ gcloud compute scp --recurse example-instance:~/narnia \
        ~/wardrobe --zone=us-central1-a

To specify the project, zone, and recurse all together, run:

    $ gcloud compute scp --project="my-gcp-project" \
        --zone="us-east1-b" --recurse ~/foo-folder/ gcp-instance-name:~/

You can limit the allowed time to ssh. For example, to allow a key to be
used through 2019:

    $ gcloud compute scp --recurse example-instance:~/narnia \
        ~/wardrobe --ssh-key-expiration="2020-01-01T00:00:00:00Z"

Or alternatively, allow access for the next two minutes:

    $ gcloud compute scp --recurse example-instance:~/narnia \
        ~/wardrobe --ssh-key-expire-after=2m

To use the IP address of your remote VM (eg, for on-prem), you must also
specify the --region and --network flags:

    $ gcloud compute scp 10.1.2.3:~/narnia ~/wardrobe \
        --region=us-central1 --network=default
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/scp)

---
### `gcloud compute sign-url`

Sign specified URL for use with Cloud CDN Signed URLs

gcloud compute sign-url generates a signed URL for the specified URL and
optionally validates the response by sending a request to the signed URL.

Cloud CDN Signed URLs give you a way to serve responses from the globally
distributed CDN cache, even if the request needs to be authorized.

Signed URLs are a mechanism to temporarily give a client access to a
private resource without requiring additional authorization. To achieve
this, the full request URL that should be allowed is hashed and
cryptographically signed. By using the signed URL you give it, that one
request will be considered authorized to receive the requested content.

Generally, a signed URL can be used by anyone who has it. However, it is
usually only intended to be used by the client that was directly given the
URL. To mitigate this, they expire at a time chosen by the issuer. To
minimize the risk of a signed URL being shared, it is recommended that the
signed URL be set to expire as soon as possible.

A 128-bit secret key is used for signing the URLs.

The URLs to sign have the following restrictions:

  o The URL scheme must be either HTTP or HTTPS.
  o The URLs must not contain the query parameters: Expires, KeyName or
    Signature, since they are used for signing.
  o The URL must not have a fragment.

**Synopsis:**
```
gcloud compute sign-url URL --expires-in=EXPIRES_IN
    --key-file=LOCAL_FILE_PATH --key-name=KEY_NAME [--validate]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   The URL to sign.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--expires-in` | EXPIRES_IN |  | The duration for which the signed URL will be valid. For example, specifying 12h will cause the signed URL to be valid up to 12 hours. See $ gcloud topic datetimes for information on duration formats. |
| `--key-file` | LOCAL_FILE_PATH |  | The file containing the RFC 4648 Section 5 base64url encoded 128-bit secret key for Cloud CDN Signed URL. It is vital that the key is strongly random. One way to generate such a key is with the following command: head -c 16 /dev/random \| base64 \| tr +/ -_ > [KEY_FILE_NAME] |
| `--key-name` | KEY_NAME |  | Name of the Cloud CDN Signed URL key. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--validate` |  |  | If provided, validates the generated signed URL by sending a HEAD request and prints out the HTTP response code. If the signed URL is valid, the result should be the same as the response code sent by the backend. If it isn't, recheck the key name and the contents of the key file, and ensure that expires-in is set to at least several seconds and that the clock on the computer running this command is accurate. If not provided, the generated signed URL is not verified. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/sign-url)

---
### `gcloud compute ssh`

SSH into a virtual machine instance

gcloud compute ssh is a thin wrapper around the ssh(1) command that takes
care of authentication and the translation of the instance name into an IP
address.

To use SSH to connect to a Windows VM, refer to this guide:
https://cloud.google.com/compute/docs/connect/windows-ssh

The default network comes preconfigured to allow ssh access to all VMs. If
the default network was edited, or if not using the default network, you
may need to explicitly enable ssh access by adding a firewall-rule:

    $ gcloud compute firewall-rules create --network=NETWORK \
        default-allow-ssh --allow=tcp:22

gcloud compute ssh ensures that the user's public SSH key is present in the
project's metadata. If the user does not have a public SSH key, one is
generated using ssh-keygen(1) (if the --quiet flag is given, the generated
key will have an empty passphrase).

If the --region and --network flags are provided, then --plain and
--tunnel-through-iap are implied and an IP address must be supplied instead
of an instance name. This is most useful for connecting to on-prem
resources.

**Synopsis:**
```
gcloud compute ssh [USER@]INSTANCE [--command=COMMAND]
    [--container=CONTAINER] [--dry-run] [--force-key-file-overwrite]
    [--plain] [--ssh-flag=SSH_FLAG] [--ssh-key-file=SSH_KEY_FILE]
    [--strict-host-key-checking=STRICT_HOST_KEY_CHECKING] [--troubleshoot]
    [--zone=ZONE] [--internal-ip | --tunnel-through-iap]
    [--network=NETWORK --region=REGION : --dest-group=DEST_GROUP]
    [--ssh-key-expiration=SSH_KEY_EXPIRATION
      | --ssh-key-expire-after=SSH_KEY_EXPIRE_AFTER] [GCLOUD_WIDE_FLAG ...]
    [-- SSH_ARGS ...]
```

**Positional arguments:**
```
[USER@]INSTANCE
   Specifies the instance to SSH into.

   USER specifies the username with which to SSH. If omitted, the user
   login name is used. If using OS Login, USER will be replaced by the OS
   Login user.

   INSTANCE specifies the name of the virtual machine instance to SSH
   into.

[-- SSH_ARGS ...]
   Flags and positionals passed to the underlying ssh implementation.

   The '--' argument must be specified between gcloud specific args on the
   left and SSH_ARGS on the right. Example:

       $ gcloud compute ssh example-instance --zone=us-central1-a -- -vvv \
       -L 80:%INSTANCE%:80
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--command` | COMMAND |  | A command to run on the virtual machine. Runs the command on the target instance and then exits. |
| `--container` | CONTAINER |  | The name or ID of a container inside of the virtual machine instance to connect to. This only applies to virtual machines that are using a Google Container-Optimized virtual machine image. For more information, see https://cloud.google.com/compute/docs/containers. |
| `--dry-run` |  |  | Print the equivalent scp/ssh command that would be run to stdout, instead of executing it. |
| `--force-key-file-overwrite` |  |  | If enabled, the gcloud command-line tool will regenerate and overwrite the files associated with a broken SSH key without asking for confirmation in both interactive and non-interactive environments. If disabled, the files associated with a broken SSH key will not be regenerated and will fail in both interactive and non-interactive environments. |
| `--plain` |  |  | Suppress the automatic addition of ssh(1)/scp(1) flags. This flag is useful if you want to take care of authentication yourself or use specific ssh/scp features. |
| `--ssh-flag` | SSH_FLAG |  | Additional flags to be passed to ssh(1). It is recommended that flags be passed using an assignment operator and quotes. Example: $ gcloud compute ssh example-instance --zone=us-central1-a \ --ssh-flag="-vvv" --ssh-flag="-L 80:localhost:80" This flag will replace occurences of %USER%, %INSTANCE%, and %INTERNAL% with their dereferenced values. For example, passing 80:%INSTANCE%:80 into the flag is equivalent to passing 80:162.222.181.197:80 to ssh(1) if the external IP address of 'example-instance' is 162.222.181.197. If connecting to the instance's external IP, then %INSTANCE% is replaced with that, otherwise it is replaced with the internal IP. %INTERNAL% is always replaced with the internal interface of the instance. |
| `--ssh-key-file` | SSH_KEY_FILE |  | The path to the SSH key file. By default, this is ~\.ssh\google_compute_engine. |
| `--strict-host-key-checking` | one of: yes, no, ask |  | Override the default behavior of StrictHostKeyChecking for the connection. By default, StrictHostKeyChecking is set to 'no' the first time you connect to an instance, and will be set to 'yes' for all subsequent connections. STRICT_HOST_KEY_CHECKING must be one of: yes, no, ask. |
| `--troubleshoot` |  |  | If you can't connect to a virtual machine (VM) instance using SSH, you can investigate the problem using the --troubleshoot flag: $ gcloud compute ssh VM_NAME --zone=ZONE \ --troubleshoot [--tunnel-through-iap] The troubleshoot flag runs tests and returns recommendations for the following types of issues: * VM status * Network connectivity * User permissions * Virtual Private Cloud (VPC) settings * VM boot If you specify the --tunnel-through-iap flag, the tool also checks IAP port forwarding. |
| `--zone` | ZONE |  | Zone of the instance to connect to. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |
| `--network` | NETWORK |  | _[(https://cloud.google.com/iap/docs/tcp-forwarding-overview).]_ Configures the VPC network to use when connecting via IP address or FQDN. |
| `--region` | REGION |  | _[(https://cloud.google.com/iap/docs/tcp-forwarding-overview).]_ Configures the region to use when connecting via IP address or FQDN. |
| `--dest-group` | DEST_GROUP |  | _[(https://cloud.google.com/iap/docs/tcp-forwarding-overview).]_ Configures the destination group to use when connecting via IP address or FQDN. |


**Examples:**
```bash
To SSH into 'example-instance' in zone us-central1-a, run:

    $ gcloud compute ssh example-instance --zone=us-central1-a

You can also run a command on the virtual machine. For example, to get a
snapshot of the guest's process tree, run:

    $ gcloud compute ssh example-instance --zone=us-central1-a \
        --command="ps -ejH"

When running a command on a virtual machine, a non-interactive shell will
typically be used. (See the INVOCATION section of
https://linux.die.net/man/1/bash for an overview.) That behavior can be
overridden by specifying a shell to run the command, and passing the -t
flag to SSH to allocate a pseudo-TTY. For example, to see the environment
variables set during an interactive session, run:

    $ gcloud compute ssh example-instance --zone=us-central1-a \
        --command="bash -i -c env" -- -t

If you are using the Google Container-Optimized virtual machine image, you
can SSH into one of your containers with:

    $ gcloud compute ssh example-instance --zone=us-central1-a \
        --container=CONTAINER

You can limit the allowed time to ssh. For example, to allow a key to be
used through 2019:

    $ gcloud compute ssh example-instance --zone=us-central1-a \
        --ssh-key-expiration="2020-01-01T00:00:00:00Z"

Or alternatively, allow access for the next two minutes:

    $ gcloud compute ssh example-instance --zone=us-central1-a \
        --ssh-key-expire-after=2m

To use the IP address of your remote VM (eg, for on-prem), you must also
specify the --region and --network flags:

    $ gcloud compute ssh 10.1.2.3 --region=us-central1 --network=default
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/ssh)

---
### `gcloud compute start-iap-tunnel`

Starts an IAP TCP forwarding tunnel

Starts a tunnel to Cloud Identity-Aware Proxy for TCP forwarding through
which another process can create a connection (eg. SSH, RDP) to a Google
Compute Engine instance.

To learn more, see the IAP for TCP forwarding documentation
(https://cloud.google.com/iap/docs/tcp-forwarding-overview).

If the --region and --network flags are provided, then an IP address or
FQDN must be supplied instead of an instance name. This is most useful for
connecting to on-prem resources.

**Synopsis:**
```
gcloud compute start-iap-tunnel INSTANCE_NAME INSTANCE_PORT
    [--iap-tunnel-disable-connection-check]
    [--local-host-port=LOCAL_HOST_PORT; default="localhost:0"]
    [--zone=ZONE]
    [--network=NETWORK --region=REGION : --dest-group=DEST_GROUP]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances

INSTANCE_PORT
   The name or number of the instance's port to connect to.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--iap-tunnel-disable-connection-check` |  |  | Disables the immediate check of the connection. |
| `--local-host-port` | LOCAL_HOST_PORT | localhost:0 | LOCAL_HOST:LOCAL_PORT on which gcloud should bind and listen for connections that should be tunneled. LOCAL_PORT may be omitted, in which case it is treated as 0 and an arbitrary unused local port is chosen. The colon also may be omitted in that case. If LOCAL_PORT is 0, an arbitrary unused local port is chosen. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |
| `--network` | NETWORK |  | Configures the VPC network to use when connecting via IP address or FQDN. |
| `--region` | REGION |  | Configures the region to use when connecting via IP address or FQDN. |
| `--dest-group` | DEST_GROUP |  | Configures the destination group to use when connecting via IP address or FQDN. |


**Examples:**
```bash
To open a tunnel to the instances's RDP port on an arbitrary local port,
run:

    $ gcloud compute start-iap-tunnel my-instance 3389

To open a tunnel to the instance's RDP port on a specific local port, run:

    $ gcloud compute start-iap-tunnel my-instance 3389 \
        --local-host-port=localhost:3333

To use the IP address or FQDN of your remote VM (eg, for on-prem), you must
also specify the --region and --network flags:

    $ gcloud compute start-iap-tunnel 10.1.2.3 3389 \
        --region=us-central1 --network=default
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/start-iap-tunnel)

---