# gcloud cloud-shell (top-level commands)

### `gcloud cloud-shell get-mount-command`

Prints a command to mount the Cloud Shell home directory via sshfs

gcloud cloud-shell get-mount-command starts your Cloud Shell if it is not
already running, then prints out a command that allows you to mount the
Cloud Shell home directory onto your local file system using sshfs. You
must install and run sshfs yourself.

After mounting the Cloud Shell home directory, any changes you make under
the mount point on your local file system will be reflected in Cloud Shell
and vice-versa.

**Synopsis:**
```
gcloud cloud-shell get-mount-command MOUNT_DIR [--force-key-file-overwrite]
    [--ssh-key-file] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MOUNT_DIR
   Local directory onto which the Cloud Shell home directory should be
   mounted.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force-key-file-overwrite` |  |  | If enabled gcloud will regenerate and overwrite the files associated with a broken SSH key without asking for confirmation in both interactive and non-interactive environment. If disabled gcloud will not attempt to regenerate the files associated with a broken SSH key and fail in both interactive and non-interactive environment. |
| `--ssh-key-file` |  |  | The path to the SSH key file. By default, this is ~/.ssh/google_compute_engine. |


**Examples:**
```bash
To print a command that mounts a remote directory onto your local file
system, run:

    $ gcloud cloud-shell get-mount-command REMOTE-DIR
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/cloud-shell/get-mount-command)

---
### `gcloud cloud-shell scp`

Copies files between Cloud Shell and the local machine

gcloud cloud-shell scp copies files between your Cloud Shell instance and
your local machine using the scp command.

**Synopsis:**
```
gcloud cloud-shell scp (cloudshell|localhost):SRC
    [(cloudshell|localhost):SRC ...] (cloudshell|localhost):DEST
    [--dry-run] [--force-key-file-overwrite] [--recurse]
    [--scp-flag=SCP_FLAG] [--ssh-key-file] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
(cloudshell|localhost):SRC [(cloudshell|localhost):SRC ...]
   Specifies the files to copy.

(cloudshell|localhost):DEST
   Specifies a destination for the source files.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dry-run` |  |  | If provided, prints the command that would be run to standard out instead of executing it. |
| `--force-key-file-overwrite` |  |  | If enabled gcloud will regenerate and overwrite the files associated with a broken SSH key without asking for confirmation in both interactive and non-interactive environment. If disabled gcloud will not attempt to regenerate the files associated with a broken SSH key and fail in both interactive and non-interactive environment. |
| `--recurse` |  |  | Upload directories recursively. |
| `--scp-flag` | SCP_FLAG |  | Extra flag to be sent to scp. This flag may be repeated. |
| `--ssh-key-file` |  |  | The path to the SSH key file. By default, this is ~/.ssh/google_compute_engine. |


**Examples:**
```bash
To denote a file in Cloud Shell, prefix the file name with the string
"cloudshell:" (e.g. cloudshell:~/FILE). To denote a local file, prefix the
file name with the string "localhost:" (e.g. localhost:~/FILE). For
example, to copy a remote directory to your local machine, run:

    $ gcloud cloud-shell scp cloudshell:~/REMOTE-DIR \
      localhost:~/LOCAL-DIR

In the above example, ~/REMOTE-DIR from your Cloud Shell instance is copied
into the ~/LOCAL-DIR directory.

Conversely, files from your local computer can be copied into Cloud Shell:

    $ gcloud cloud-shell scp localhost:~/LOCAL-FILE-1 \
      localhost:~/LOCAL-FILE-2 cloudshell:~/REMOTE-DIR

Under the covers, scp(1) or pscp (on Windows) is used to facilitate the
transfer.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/cloud-shell/scp)

---
### `gcloud cloud-shell ssh`

Allows you to establish an interactive SSH session with Cloud Shell

gcloud cloud-shell ssh lets you remotely log in to Cloud Shell. If your
Cloud Shell is not currently running, this will cause it to be started
before establishing the SSH session.

**Synopsis:**
```
gcloud cloud-shell ssh [--authorize-session] [--command=COMMAND]
    [--dry-run] [--force-key-file-overwrite] [--ssh-flag=SSH_FLAG]
    [--ssh-key-file] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--authorize-session` |  |  | If provided, sends OAuth credentials to the current Cloud Shell session on behalf of the user. When this completes, the session will be authorized to run various Google Cloud command-line tools without requiring the user to manually authenticate. |
| `--command` | COMMAND |  | A command to run in Cloud Shell. Runs the command in Cloud Shell and then exits. |
| `--dry-run` |  |  | If provided, prints the command that would be run to standard out instead of executing it. |
| `--force-key-file-overwrite` |  |  | If enabled gcloud will regenerate and overwrite the files associated with a broken SSH key without asking for confirmation in both interactive and non-interactive environment. If disabled gcloud will not attempt to regenerate the files associated with a broken SSH key and fail in both interactive and non-interactive environment. |
| `--ssh-flag` | SSH_FLAG |  | Additional flags to be passed to ssh(1). |
| `--ssh-key-file` |  |  | The path to the SSH key file. By default, this is ~/.ssh/google_compute_engine. |


**Examples:**
```bash
To SSH into your Cloud Shell, run:

    $ gcloud cloud-shell ssh

To run a remote command in your Cloud Shell, run:

    $ gcloud cloud-shell ssh --command=ls
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/cloud-shell/ssh)

---