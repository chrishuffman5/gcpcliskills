# gcloud compute os-login

create and manipulate Compute Engine OS Login resources

### `gcloud compute os-login describe-profile`

Describe the OS Login profile for the current user

gcloud compute os-login describe-profile displays the OS Login profile for
the currently authenticated user, including Posix accounts and SSH keys
associated with the user.

**Synopsis:**
```
gcloud compute os-login describe-profile [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To show all of the information about your OS Login profile, including POSIX
account information and stored SSH public keys, run:

    $ gcloud compute os-login describe-profile

To show all of the information in a different format, such as JSON, use the
--format flag:

    $ gcloud compute os-login describe-profile --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-login/describe-profile)

---
### `gcloud compute os-login remove-profile`

Remove the posix account information for the current user

gcloud compute os-login remove-profile removes the posix account
information for the current user where the account ID field is set to the
current project ID. Posix account entries for G Suite users do not set the
account ID field and can only be modified by a domain administrator.

**Synopsis:**
```
gcloud compute os-login remove-profile [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To remove all POSIX accounts associated with the current user and project,
run:

    $ gcloud compute os-login remove-profile

To remove all POSIX accounts associated with the current user in the
project named example-project, run:

    $ gcloud compute os-login remove-profile --project=example-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-login/remove-profile)

---

## `gcloud compute os-login ssh-keys` — list, add, update, and remove OS Login SSH Keys
### `gcloud compute os-login ssh-keys add`

Add an SSH public key to an OS Login profile

gcloud compute os-login ssh-keys add accepts either a string containing an
SSH public key or a filename for an SSH public key and adds that key to the
user's OS Login profile.

**Synopsis:**
```
gcloud compute os-login ssh-keys add (--key=KEY | --key-file=KEY_FILE)
    [--ttl=TTL] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | _[Exactly one of these must be specified:]_ The SSH public key to add to the OS Login Profile. |
| `--key-file` | KEY_FILE |  | _[Exactly one of these must be specified:]_ The path to a file containing an SSH public key to add to the OS Login Profile. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ttl` | TTL |  | The amount of time before the SSH key expires. For example, specifying 30m will set the expiration time on the SSH key for 30 minutes from the current time. A value of 0 will result in no expiration time. See $ gcloud topic datetimes for information on duration formats. |


**Examples:**
```bash
To add the key in /home/user/.ssh/id_rsa.pub to your OS Login profile, run:

    $ gcloud compute os-login ssh-keys add \
        --key-file=/home/user/.ssh/id_rsa.pub

To add the same key, but with a one year expiration time, run:

    $ gcloud compute os-login ssh-keys add \
        --key-file=/home/user/.ssh/id_rsa.pub --ttl=1y

To add a key not stored in a file, run:

    $ gcloud compute os-login ssh-keys add \
        --key='ssh-rsa AAAAB3NzaC1yc2EAAA...MTg+InRG47+/O4/uWEOy6gIQEF
     user@example.com'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-login/ssh-keys/add)

---
### `gcloud compute os-login ssh-keys describe`

Describe an SSH Public Key from an OS Login Profile

gcloud compute os-login ssh-keys describe accepts either a string
containing an SSH Public Key or a filename for an SSH Public key and
displays that key from the user's OS Login Profile. The key value used can
either be the full SSH key or the OS Login fingerprint for that key.

**Synopsis:**
```
gcloud compute os-login ssh-keys describe (--key=KEY | --key-file=KEY_FILE)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | _[Exactly one of these must be specified:]_ The SSH public key to describe from the OS Login Profile. Key value can either be the SSH key or the OS Login fingerprint of the key. |
| `--key-file` | KEY_FILE |  | _[Exactly one of these must be specified:]_ The path to a file containing an SSH public key to describe from the OS Login Profile. Key value can either be the SSH key or the OS Login fingerprint of the key. |


**Examples:**
```bash
To show all of the information for the key stored in your OS Login profile
that matches the key in /home/user/.ssh/id_rsa.pub, run:

    $ gcloud compute os-login ssh-keys describe \
        --key-file=/home/user/.ssh/id_rsa.pub

To show all of the information about the key with a fingerprint of
'e0d96d6fad35a61a0577f467940509b5aa08b6dea8d99456ec19a6e47126bc52', run:

    $ gcloud compute os-login ssh-keys describe \
        --key='e0d96d6fad35a61a0577f467940509b5aa08b6dea8d99456ec19a6e47\
    126bc52'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-login/ssh-keys/describe)

---
### `gcloud compute os-login ssh-keys list`

List SSH public keys from an OS Login profile

gcloud compute os-login ssh-keys list lists the SSH public keys in an OS
Login profile. By default, the command only displays the fingerprints and
experation time for the keys. Additional data can be displayed using the
--format flag.

**Synopsis:**
```
gcloud compute os-login ssh-keys list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list the keys in your OS Login profile, run:

    $ gcloud compute os-login ssh-keys list

To show all of the SSH public key information, in YAML format, run:

    $ gcloud compute os-login ssh-keys list --format=yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-login/ssh-keys/list)

---
### `gcloud compute os-login ssh-keys remove`

Remove an SSH public key from an OS Login profile

gcloud compute os-login ssh-keys remove accepts either a string containing
an SSH public key or a filename for an SSH public key and removes that key
from the user's OS Login profile. The key value used can either be the full
SSH key or the OS Login fingerprint for that key.

**Synopsis:**
```
gcloud compute os-login ssh-keys remove (--key=KEY | --key-file=KEY_FILE)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | _[Exactly one of these must be specified:]_ The SSH public key to remove from the OS Login Profile. Key value can either be the SSH key or the OS Login fingerprint of the key. |
| `--key-file` | KEY_FILE |  | _[Exactly one of these must be specified:]_ The path to a file containing an SSH public key to remove from the OS Login Profile. Key value can either be the SSH key or the OS Login fingerprint of the key. |


**Examples:**
```bash
To remove the key that is stored in /home/user/.ssh/id_rsa.pub, run:

    $ gcloud compute os-login ssh-keys remove \
        --key-file=/home/user/.ssh/id_rsa.pub

To remove the key with fingerprint
'e0d96d6fad35a61a0577f467940509b5aa08b6dea8d99456ec19a6e47126bc52', run:

    $ gcloud compute os-login ssh-keys remove \
        --key='e0d96d6fad35a61a0577f467940509b5aa08b6dea8d99456ec19a6e47\
    126bc52'

To remove the SSH public key
'AAAAB3NzaC1yc2EAAAADAQABAAAB...ZrPg+DZJIwPab2wPlveLh+ut1Lxs5QTR/9QfEa7',
run:

    $ gcloud compute os-login ssh-keys remove \
        --key='AAAAB3NzaC1yc2EAAAADAQABAAAB...ZrPg+DZJIwPab2wPlveLh+ut1L\
    xs5QTR/9QfEa7'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-login/ssh-keys/remove)

---
### `gcloud compute os-login ssh-keys update`

Update an SSH public key in an OS Login profile

gcloud compute os-login ssh-keys update accepts either a string containing
an SSH public key or a filename for an SSH public key, and updates the key
in the user's OS Login profile. Currently, only the expiration time, --ttl,
can be updated.

**Synopsis:**
```
gcloud compute os-login ssh-keys update --ttl=TTL
    (--key=KEY | --key-file=KEY_FILE) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ttl` | TTL |  | The amount of time before the SSH key expires. For example, specifying 30m will set the expiration time on the SSH key for 30 minutes from the current time. A value of 0 will result in no expiration time. See $ gcloud topic datetimes for information on duration formats. |


**Examples:**
```bash
To update the SSH public key found in /home/user/.ssh/id_rsa.pub with an
expiration time of one week from now, run:

    $ gcloud compute os-login ssh-keys update --ttl=7d \
        --key-file=/home/user/.ssh/id_rsa.pub

To update the SSH public key with a fingerprint of
'e0d96d6fad35a61a0577f467940509b5aa08b6dea8d99456ec19a6e47126bc52' and an
expiration time of five years from now, run:

    $ gcloud compute os-login ssh-keys update --ttl=5y \
        --key='e0d96d6fad35a61a0577f467940509b5aa08b6dea8d99456ec19a6e47\
    126bc52'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-login/ssh-keys/update)

---