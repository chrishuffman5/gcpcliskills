# gcloud cloud-shell — Cloud Shell

## Overview
Google Cloud Shell is a browser-accessible, ephemeral Debian-based Linux VM with pre-installed tools (gcloud CLI, Docker, Git, editors, language runtimes) and 5 GB of persistent home-directory storage per user. The `gcloud cloud-shell` command group lets you drive that environment from your local machine: open an interactive SSH session, run remote commands, copy files in either direction, and mount your Cloud Shell `$HOME` over sshfs. Reach for it when you want your local terminal and file system to interoperate with the same Cloud Shell environment you get in the Console.

## Quick reference — common workflows

### 1. Open an interactive SSH session
```bash
# Start an interactive Cloud Shell session (starts the VM if it is not running)
gcloud cloud-shell ssh

# Authorize the session so gcloud/gsutil work immediately without re-auth
gcloud cloud-shell ssh --authorize-session
```

### 2. Run a remote command non-interactively
```bash
# Run a single command in Cloud Shell and exit
gcloud cloud-shell ssh --command=ls

# Preview the underlying ssh command without executing it
gcloud cloud-shell ssh --command="gcloud version" --dry-run
```

### 3. Copy files from Cloud Shell to your local machine
```bash
# Copy a single file from Cloud Shell home to a local directory
gcloud cloud-shell scp cloudshell:~/remote-file.txt localhost:~/Downloads/

# Copy a directory recursively from Cloud Shell to local
gcloud cloud-shell scp --recurse cloudshell:~/my-project localhost:~/projects/
```

### 4. Copy files from your local machine into Cloud Shell
```bash
# Copy one or more local files into the Cloud Shell home directory
gcloud cloud-shell scp localhost:~/local-file-1.txt localhost:~/local-file-2.txt cloudshell:~/

# Preview the scp command without executing it
gcloud cloud-shell scp localhost:~/file.txt cloudshell:~/ --dry-run
```

### 5. Mount the Cloud Shell home directory via sshfs
```bash
# Print the sshfs command that mounts Cloud Shell $HOME onto a local mount point
gcloud cloud-shell get-mount-command ~/cloudshell-mount

# Run the printed command to mount (you must install and run sshfs yourself).
# Changes under the mount point are reflected in Cloud Shell and vice-versa.
```

### 6. Use a custom SSH key file
```bash
# SSH using a specific key file instead of ~/.ssh/google_compute_engine
gcloud cloud-shell ssh --ssh-key-file=~/.ssh/my_cloud_shell_key

# Regenerate and overwrite a broken SSH key without prompting
gcloud cloud-shell ssh --force-key-file-overwrite
```

## Command groups

This service has no subgroups — all commands are top-level.

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| (top-level) | [`_commands.md`](_commands.md) | `get-mount-command`, `scp`, `ssh` | SSH into, copy files to/from, and mount your Cloud Shell environment |

See [`index.md`](index.md) for a one-line index of all 3 commands.

## Common flags & tips
- **Endpoint prefixes for `scp`:** every source/destination must be prefixed with `cloudshell:` (remote) or `localhost:` (local) — e.g. `cloudshell:~/FILE` vs `localhost:~/FILE`. Multiple sources are allowed before the single destination.
- **`--dry-run`** (on `ssh` and `scp`): prints the command that would be run to stdout instead of executing it — useful for inspecting the generated `ssh`/`scp` invocation.
- **`--authorize-session`** (on `ssh`): pushes OAuth credentials into the running session so Google Cloud command-line tools work without a separate manual login.
- **`--recurse`** (on `scp`): uploads directories recursively.
- **SSH keys:** `--ssh-key-file` overrides the default key (`~/.ssh/google_compute_engine`); `--force-key-file-overwrite` regenerates a broken key without confirmation in both interactive and non-interactive environments.
- **Pass-through flags:** `--ssh-flag=SSH_FLAG` (on `ssh`) and `--scp-flag=SCP_FLAG` (on `scp`) forward extra flags to the underlying `ssh(1)`/`scp(1)`; both may be repeated. On Windows the transfer uses `pscp`.
- **Auto-start:** `ssh` and `get-mount-command` will start your Cloud Shell VM if it is not already running.
- **No regional/zonal flags:** Cloud Shell is a per-user managed environment, so there are no `--region`/`--zone` arguments on these commands.

## beta / alpha
The same three commands (`ssh`, `scp`, `get-mount-command`) exist identically under `gcloud beta cloud-shell` and `gcloud alpha cloud-shell`. No additional commands or flags are exclusive to the beta or alpha channels. (Note: the unrelated legacy `gcloud alpha shell` was renamed to `gcloud alpha interactive` and is not part of this group.)

## Official documentation
- [Cloud Shell documentation home](https://cloud.google.com/shell/docs) — product guides, reference, and resources.
- [gcloud cloud-shell command reference](https://cloud.google.com/sdk/gcloud/reference/cloud-shell) — full reference for `ssh`, `scp`, and `get-mount-command`.
- [Using Cloud Shell](https://cloud.google.com/shell/docs/using-cloud-shell) — terminal, editor, storage modes, and web preview.
- [How Cloud Shell works](https://cloud.google.com/shell/docs/how-cloud-shell-works) — architecture: per-user VMs, Docker container, 5 GB persistent `$HOME`.
- [Run gcloud commands with Cloud Shell](https://cloud.google.com/shell/docs/run-gcloud-commands) — quickstart for running gcloud in Cloud Shell.
- [Cloud Shell limitations](https://cloud.google.com/shell/docs/limitations) — quotas and limits (50 hr/week, 12 hr max session, 40 min inactivity timeout).
- [Cloud Shell REST API reference](https://cloud.google.com/shell/docs/reference/rest) — `cloudshell.googleapis.com` API (enable with `gcloud services enable cloudshell.googleapis.com` for programmatic access).
