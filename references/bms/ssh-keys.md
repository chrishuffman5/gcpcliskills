# gcloud bms ssh-keys

manage SSH keys for Bare Metal Solution

### `gcloud bms ssh-keys add`

Add a public SSH key to the project in Bare Metal Solution

Add a public SSH key to the project in Bare Metal Solution.

**Synopsis:**
```
gcloud bms ssh-keys add SSH_KEY (--key=KEY | --key-file=KEY_FILE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SSH key resource - ssh_key. This represents a Cloud resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument ssh_key on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the region attribute:
 * provide the argument ssh_key on the command line with a fully
   specified name;
 * global is the only supported location.

This must be specified.

  SSH_KEY
     ID of the SSH key or fully qualified identifier for the SSH key.

     To set the ssh_key attribute:
     + provide the argument ssh_key on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | _[Exactly one of these must be specified:]_ The SSH public key to add |
| `--key-file` | KEY_FILE |  | _[Exactly one of these must be specified:]_ The path to a file containing an SSH public key to add |


**Examples:**
```bash
To add an SSH key called my-ssh-key in project my-project with a public key
ABC6695

    $ gcloud bms ssh-keys add my-ssh-key --project=my-project \
        --key=ABC6695

To add an SSH key called my-ssh-key in project my-project with a public key
stored in /home/user/.ssh/id_rsa.pub

    $ gcloud bms ssh-keys add my-ssh-key --project=my-project \
        --key-file=/home/user/.ssh/id_rsa.pub
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/ssh-keys/add)

---
### `gcloud bms ssh-keys list`

List the SSH keys added to the project in Bare Metal Solution

List the SSH keys added to the project in Bare Metal Solution.

**Synopsis:**
```
gcloud bms ssh-keys list [--filter=EXPRESSION] [--limit=LIMIT]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all SSH keys within the project, run:

    $ gcloud bms ssh-keys list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/ssh-keys/list)

---
### `gcloud bms ssh-keys remove`

Remove an SSH key in Bare Metal Solution given its name

Remove an SSH key in Bare Metal Solution given its name.

**Synopsis:**
```
gcloud bms ssh-keys remove SSH_KEY [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SSH key resource - ssh_key. This represents a Cloud resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument ssh_key on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the region attribute:
 * provide the argument ssh_key on the command line with a fully
   specified name;
 * global is the only supported location.

This must be specified.

  SSH_KEY
     ID of the SSH key or fully qualified identifier for the SSH key.

     To set the ssh_key attribute:
     + provide the argument ssh_key on the command line.
```

**Examples:**
```bash
To remove an SSH key called my-ssh-key run:

    $ gcloud bms ssh-keys remove my-ssh-key
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/ssh-keys/remove)

---